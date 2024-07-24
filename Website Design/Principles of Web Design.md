
## 1 Content
- Fresh and interesting
- Quality more important than quantity
- Not just copy & paste onto a server
- Concentrate on your best material
- Have a voice (active not passive)

## 2 Organisation and Navigation
- Map out everything
- Seperate content (play around with arrangements)
- Avoid metaphors (no road signs etc)
- Design for what users will expect
- Allow easy access to breadth and width of site

### 2.1 Navigation 
Focusses on how a user moves through your site and how a user knows where they are and how to find the information theyre looking for

![500](Pasted%20image%2020240321221344.png)

![500](Pasted%20image%2020240321221409.png)

## 3 Visual Design
- Consistency throughout
- High-quality, professional
- Customer experience builds brand

### 3.1 Typography
- Small section, 1-3
- Use ti show hierarchy
- Check out www.typespiration.com

### 3.2 Colour
- use a palette of 3-5 colours
- use high contrast sparingly

### 3.3 Layout
- Start with a grid
- Keep stuff balanced
- Add padding between edge and text
- Make use of white space
- Create hierarchy with size

## 4 Performance
- Fast sites are successful sites
- Trade off (speed/elaboration)
- How is your audience accessing the site
- Consider total page size

### 4.1 Tips
- Use CSS rather than text graphics
- GIF/PNG for graphics, jpeg for photos
- Imagine optimisation
	- Serve scaled images
	- Experiment with quality settings
- Reuse graphical elements

## 5 Compatibility
- Site works and displays properly across browsers
- Cutting edge is not always the best option
- Can everyone see the content
- Are multiple formats required for photo/video content
	- transcoding allows for optimisation
- Some techniques are not widely supported, such as flexbox which has limited support on some browsers

## 6 Interactivity
- Know your target users and their expectations in relations to your site/product
- A unique site that is incongruous what thats familiar disrupts their workflow and causes confusion
- People are not on your site to work to get answers
- Include links to other resources that are directly relevant to the current location

## 7 Design
Try and spend as much time as possible in designing. Flesh out wireframes and prototype the site:
- For wireframing, [Wireframe.cc](https://wireframe.cc) can be used
- Prototyping/mockup:
	- UXPIN
	- InVision
	- Axure RP
	- Sketch
	- Photoshop


## 8 Responsive Design
It is not just making a site mobile or making everything smaller. It is taking advantage of features on different devices e.g.
- extra sensors on phone or smart watch
- Larger screen real estate on website 
It also means adapting to the pitfalls, e.g. smaller screen real-estate by:
- Resizing fonts, layouts and images
- Hiding content
- Re-prioritising content and adjusting layouts
- Thinking about interaction, e.g. no hover on mobile
- Optimising images and resources for the device + bandwidth

For more information check out [Google Developer Web Design Patterns](https://web.dev/learn/design/?hl=en)

**Progressive enhancement** refers to building a basic website then adding new features as needed.
Must ensure that the site allows for **graceful degradation**, so when a user comes along whos browser does not support all the fancy features, their experience is still respectable.

#### 8.1.1 Mobile first or desktop first
- What is the sites purpose
- How complex is this
- Where/how will the site be used

### 8.2 Implementing Responsive design
- Use relative units
	- % relative to parent
	- vw, vh - relative ti viewpoint
	- em - relative to font size
- Use media queries
- 