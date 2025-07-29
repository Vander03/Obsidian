## 1 Implementation 1
didnt account for the accumulator storing the result in `x`, split it up into multiple
```F#
let feedforwardOneLayer (model: Model) (keyCache:MultiHead[][]) (valueCache:MultiHead[][]) (tokenPosition:int) (input: Vector) (layer: int) : Vector * MultiHead * MultiHead =
    // TODO: Implement this function.
    // start of loop
    // normalize
    let norm = rootMeanSquareNormalize model.weights.[layer].normalizeInputWeights input
    
    // determine query, key and value
    let query =
            matrixMultiply model.weights.[layer].wq norm
            |> reshapeToMultipleHeads model.headSize
            |> rotateVector model.rotationCoefficients.[layer]

    
    let key =
          matrixMultiply model.weights.[layer].wk norm
          |> reshapeToMultipleHeads model.headSize
          |> rotateVector model.rotationCoefficients.[layer]
          
    let value =
        matrixMultiply model.weights.[layer].wv norm
        |> reshapeToMultipleHeads model.headSize
    
    // populate keychache and valuecache          
    let keyLookup = createLookupFunction keyCache key tokenPosition layer
    let valueLookup = createLookupFunction valueCache value tokenPosition layer
    
    // calculate attention using lookup functions
    let att =
        attention keyLookup valueLookup tokenPosition query
        |> matrixMultiply model.weights.[layer].wo
        |> add input
        |> rootMeanSquareNormalize model.weights.[layer].normalizeAttentionWeights
    
    let ff1 = matrixMultiply model.weights.[layer].w1 att |> sigmoidActivation
    let ff3 = matrixMultiply model.weights.[layer].w3 att
    // element-wise multiply them for the gating
    let ffGated = elementWiseMultiply ff1 ff3
    let ff2 = matrixMultiply model.weights.[layer].w2 ffGated
    
    let out = add input ff2  // second residual
    
    // Return the final vector plus key and value vectors
    (out, key, value)

```


