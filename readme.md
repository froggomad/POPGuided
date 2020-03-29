# Protocol Oriented Programming Guided Project

## Directions

### Group Structure (MVC)

- [ ]  Click your AppDelegate file, **hold cmd**
    - [ ]  Click your SceneDelegate file
    - [ ]  Click your Assets.xcassets file, **let go of cmd**
    - [ ]  Right click (or 2-finger, ctrl-click) and select New Group From Selection
    - [ ]  Name the group whatever you'd like, but try to keep it semantic
        - [ ]  Resources, Supporting Files, Assets are a few good choices. I'm going to call mine Resources
- [ ]  Click your topmost folder (same name as your project, but *not* the blue one
    - [ ]  Cmd-option-N
        - [ ]  or right-click, or control/2-finger click and select New Group
    - [ ]  Name this group Model or Models (I prefer Singular to match MVC exactly... but I'm kinda weird)
- [ ]  Click your Main.Storyboard, **hold cmd**
    - [ ]  Click your LaunchScreen.storyboard
    - [ ]  ctrl-click, 2-finger click, or right-Click one of the storyboard files and select New Group From Selection
    - [ ]  name this group Storyboards
- [ ]  ctrl-click, 2-finger click, or right-Click the Storyboards group
    - [ ]  Name this View or Views (Again, I'm weird , I prefer singular here - you do whatever suits you)
- [ ]  ctrl-click, 2-finger click, or right-Click your ViewController.swift file
    - [ ]  Select New Group From Selection
    - [ ]  Name this View Controllers (plural)
- [ ]  ctrl-click, 2-finger click, or right-Click your View Controllers Group
    - [ ]  Select New Group From Selection
    - [ ]  Name this Controller or Controllers (again, I'm weird, so you can guess what I do here)
- [ ]  New File in Model Group called CarParts.swift
    - [ ]  enum Engine
        - [ ]  🛑 explain why we're using an enum (convenience, safety)
    - [ ]  enum Body
    - [ ]  enum Make: String
        - [ ]  🛑 talk about rawValue and why
    - [ ]  enum Model: String
- [ ]  New File in Model Group called Protocols.swift
    - [ ]  protocol Vehicle
        - [ ]  🛑 explain how a protocol defines requirements for something to follow
    - [ ]  protocol Drivable
        - [ ]  Not all vehicles are drivable, but all drivable are vehicles
        - [ ]  🛑 note 2
    - [ ]  New File in Model Group called Car.swift
        - [ ]  struct Car: Drivable
            - [ ]  🛑 Talk about conformance
    - [ ]  Re-name ViewController class using refactor → rename (CarListingController.swift)
        - [ ]  🛑 ask about red filename or error sound
    - [ ]  Clean up unused comments (leave prepare(for segue: ...) method)

### Storyboard

- [ ]  Embed ViewController in Navigation Controller
- [ ]  Assign class in storyboard
- [ ]  Drag out UICollectionView pin 8 8 8 8
- [ ]  Give cell an identifier
- [ ]  Drag 2 labels into cell (top and bottom)
- [ ]  Use left menu to make constraints
    - [ ]  Top Label: 8 top, center horizontally → Content View
    - [ ]  Btm Label: 8 btm, center horizontally → Content View

### View Controller

- [ ]  Connect CollectionView to ViewController

### Custom Cell

- [ ]  Right click View Group New File
    - [ ]  Make new UICollectionViewCell CocoaTouch file
    - [ ]  Name it VehicleCollectionViewCell
    - [ ]  Give it an optional property of type Vehicle to hold a vehicle the cell will use to update itself
        - [ ]  🛑 ask if anyone can tell me why it's optional
        - [ ]  Implement DidSet
            - [ ]  🛑 Explain DidSet
    - [ ]  stub func updateViews()
- [ ]  Assign Class to Cell in Storyboard
- [ ]  **IBOutlets**
- [ ]  Both UILabels → Cell
- [ ]  Implement updateViews()
    - [ ]  Guard unwrap labels
        - [ ]  talk about labels being optional
    - [ ]  Talk about guard soldier

### Back To VehicleListingsVC

- [ ]  create class array to hold cars of type Vehicle (use this for data source)
- [ ]  In viewDidLoad:
    - [ ]  create instances of Car and Beater
    - [ ]  add to vehicle array
- [ ]  extension CarListingsViewController: UICollectionViewDelegate, UICollectionViewDataSource
    - [ ]  🛑 explain protocol
    - [ ]  Implement cellForItemAt
        - [ ]  🛑 notice, item not row (collectionView can have multiple items in one row)
        - [ ]  do it without downcasting and ask why I can't access .vehicle
        - [ ]  🛑 downcast without guard let at first, explain why its optional
    - [ ]  Implement numberOfItemsInSection
        - [ ]  🛑 what do you think we should return here?
        - [ ]  return arr.count (explain implicit return)
    - [ ]  🛑 run the app
        - [ ]  ask why people think there are no cells
        - [ ]  Implement the delegates
    - [ ]  🛑 run the app
        - [ ]  ask why people think the content is being cut off
        - [ ]  explain that by default the cells will attempt to display all of the content within the constraints you set, and we didn't set any constraints for the leading or trailing bounds of the labels
    - [ ]  Set the leading and trailing to 8 (use content view in side menu)
    - [ ]  🛑 run the app
        - [ ]  ask if anyone can figure out why the labels are so close together
        - [ ]  explain that again, we didn't define how far apart we want them to be so the cell is shrinking to the size of its content.
    - [ ]  Set the vertical between labels to 60 or something reasonable
    - [ ]  🛑 run the app
- [ ]  Back to protocol extension Vehicle (default implementation... nice)
