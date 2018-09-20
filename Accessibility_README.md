# QA Accessiblity Testing For Mobile Apps

## What is Accessibility?

Accessibility is a program native to mobile devices that allows physically and visually impared users to interact with their device. The user is then read a selected portion of the focused element. Then, through different gestures, the user is able to complete intended tasks.

### **How to use**

- Turn it on
  - _**Always do this before you enter the app you are testing. The selector can be manipulated in ways that would mess up the test case if turned on within the app**_
  - Accessibility can be found in the "Settings" of a device. Path tends to be `Settings -> Accessibility -> Vision`
    - For android, accessibility is usually referred to as "Talk Back"
    - iOS accessibility is usually referred to as "Voice Over"
    - **Tip:** Shortcuts can be used for accessibility.
      - Android: _(If available)_ Holding down a combination of buttons for a few seconds.
      - iOS: Triple clicking the home button. (Side button for iPhone X)
        - Needs to be manually turned on for iOS

- Navigation
  - To navigate through the apps by:
    - Swiping left or right to cycle through different elements.
    - Dragging your finger across the screen to different elements.
  - To "pan" through the app:
    - On Android you can use two fingers to drag the page up or down.
    - On iOS you can drag three fingers up or down to `page up` or `page down`.

- Modes
  - To change to a different mode:
    - iOS: Use two fingers on the screen and twist in a clockwise/counter clockwise motion. Changes what is referred to as the "rotor" in Apple docs.
    - Android: Swipe up or down.
  - To use accessibility in the selected mode:
    - iOS: Swipe up or down.
    - Android: Swipe left or right normally.
  - There are different options for what the selector navigates. There are some variations but the general ones are as follows:
    - Words
      - Iterates through each word.
    - Lines
      - Iterates through lines (not really available throughout the app).
    - Links
      - Iterates through links (again not available thorughout app).
    - Headings(ios)/... And Landmarks (Android)
      - Iterates through headings (not really available throughout app).
    - Actions(iOS (not available in app))/Controls(Android)
      - Iterates through elements with available actions (buttons, etc...) skipping headers and other text.
  - Here are a few specific to iOS:
    - Containers
      - Iterates through container elements. (Can be used to jump to the top of the page in the app).
    - Speaking Rate
      - Modify speaking rate
    - Form Controls
      - Sort of like actions in that, for the app, it iterates through different actionable items (cart, other buttons, pdps, etc...).
  - Here are a few specific to Android:
    - Default
      - Iterates through elements. Very basic.

- Select
  - To select normal elements or enter into text/form fields, you can simply double tap while the selector is on said element.
  - For keyboards, Android defaults to single tap activation (you don't need to select the key and then double tap to enter the character you selected) however, iOS does not. If you want you can manually activate this option `Settings -> General -> Accessibility -> VoiceOver -> Typing Style -> Touch Typing/Direct`

___

### **Things to look for**

- Aria Labels
  - Selectable elements should have an `aria-label` which is read by the accessibility program.

  - Aria-label:<br>![aria-label](https://github.com/CoryWritesCode/accessibility_resource/blob/master/aria-label.PNG "Aria-Label")

- Where is the focus
  - Focus (the box telling you visually where the selector is) should be on the selector and not over extended, which could lead to issues.

  - **BAD:** Focus Overflow:<br>![focus_overflow](https://github.com/CoryWritesCode/accessibility_resource/blob/master/the_worst.PNG "Focus Overflow")
    - *In the case above the accessibility might select `Checkout` instead of the intended `Add` button.*
  - **Good** Good Focus:<br>![focus_overflow](https://github.com/CoryWritesCode/accessibility_resource/blob/master/good_focus.PNG "Focus Overflow")

- What is being read
  - **Things to be read**
    - If the element is selectable. (buttons, etc...)
    - Any relevant info the element contains. (disclaimers, product details, etc...)
    - Relevant information related to an action that was taken. (If item was added/deleted, what item was it)
  - **Things not to be read**
    - Direct names of irelevant elements. (`<p>`, `<div>`, etc...)

- Navigating through the Experience
  - Ability
    - You want to make sure **every** button and readable object is able to be selected.
      - Good rule of thumb: If I can see it as a sighted person, then VO/TB should be able to focus it.
  - Flow
    - You want to make sure the user's arn't having to do too much to get to where they want to go.
      - i.e. Don't make the `Add to cart` button selectable only when they have to scroll through 15 things and have to switch their modes twice to get there.
      - **Tip:** Take some time to go through the app while __not__ looking at it. It's weird at first but it will give you a good indication if you know something is there but it's not being selected or it seems hard to get to.

___

### **Examples**

- Checking my virality code.
  1. Turn on VO/TB.
  2. Navigate to member app.
  3. Navigate to virality code.
  4. Place focus on virality code.
  5. Change mode to iterate through characters.
  6. Iterate through each character. VO/TB will notate if the individual charater is `capital`.

___

### **Resources**

- [iOS gesture list (short)](https://www.applevis.com/guides/ios-voiceover/complete-list-ios-gestures-available-voiceover-users)
- [iOS gesture list (verbose)](https://support.sas.com/misc/accessibility/education/ios/quickref.html)
- [Android Gesture list](http://pauljadam.com/demos/talkbackcheatsheet.html)