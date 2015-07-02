KolodaView
--------------

[![Yalantis](https://raw.githubusercontent.com/Yalantis/PullToMakeSoup/master/PullToMakeSoupDemo/Resouces/badge_dark.png)](http://Yalantis.com/?utm_source=github)

Check this [article on our blog](https://yalantis.com/blog/how-we-built-tinder-like-koloda-in-swift/)

![Preview](https://github.com/Yalantis/Koloda/blob/master/Koloda_example_animation.gif)

Purpose
--------------

KolodaView is a class designed to simplify the implementation of Tinder like cards on iOS. It adds convenient functionality such as a UITableView-style dataSource/delegate interface for loading views dynamically, and efficient view loading, unloading .

Supported OS & SDK Versions
-----------------------------

* Supported build target - iOS 8.0 (Xcode 6.2)


ARC Compatibility
------------------

KolodaView requires ARC. 


Thread Safety
--------------

KolodaView is subclassed from UIView and - as with all UIKit components - it should only be accessed from the main thread. You may wish to use threads for loading or updating KolodaView contents or items, but always ensure that once your content has loaded, you switch back to the main thread before updating the KolodaView.

Installation
--------------
To install via CocoaPods add this line to your Podfile

pod "KolodaView"


To install manually the KolodaView class in an app, just drag the KolodaView, DraggableCardView, OverlayView class files (demo files and assets are not needed) into your project. Also you need to install facebook-pop. Or add bridging header if you are using CocoaPods.


Properties
--------------

The KolodaView has the following properties:
```swift
	weak var dataSource: CardDeckViewDataSource!
```
An object that supports the CardDeckViewDataSource protocol and can provide views to populate the KolodaView.
```swift
	weak var delegate: CardDeckViewDelegate?
```
An object that supports the CardDeckViewDelegate protocol and can respond to KolodaView events.
```swift
    public var currentCardNumber
```
The index of front card in the KolodaView (read only).
```swift
    public var countOfCards
```    
The count of cards in the KolodaView (read only). To set this, implement the `deckNumberOfCards:` dataSource method. 
```swift
    var countOfVisibleCards
```
The count of displayed cards in the KolodaView.
	
Methods
--------------

The KolodaView class has the following methods:
```swift
	func reloadData()
```
This reloads all KolodaView item views from the dataSource and refreshes the display.
```swift
	func revertAction()
```	
Applies undo animation and decrement currentCardNumber.
```swift
	func applyAppearAnimation()
```
Applies appear animation.
```swift
	func swipeLeft() 
```
Applies swipe left animation and action, increment currentCardNumber.
```swift
	func swipeRight()
```
Applies swipe right animation and action, increment currentCardNumber.

Protocols
---------------

The KolodaView follows the Apple convention for data-driven views by providing two protocol interfaces, CardDeckViewDataSource and CardDeckViewDelegate. The CardDeckViewDataSource protocol has the following methods:
```swift
	func deckNumberOfCards(deck: KolodaView) -> UInt
```
Return the number of items (views) in the KolodaView.
```swift
	func deckViewForCardAtIndex(deck: KolodaView, index: UInt) -> UIView
```
Return a view to be displayed at the specified index in the KolodaView. 
```swift
   func deckViewForCardOverlayAtIndex(deck: KolodaView, index: UInt) -> OverlayView?
```   
Return a view for card overlay at the specified index. For setting custom overlay action on swiping(left/right), you should override didSet of overlayState property in OverlayView. (See Example)

The CardDeckViewDelegate protocol has the following methods:
```swift    
    func deckDidSwipedCardAtIndex(deck: KolodaView,index: UInt, direction: SwipeResultDirection)
```    
This method is called whenever the KolodaView swipes card. It is called regardless of whether the card was swiped programatically or through user interaction.
```swift
    func deckDidRunOutOfCards(deck: KolodaView)
```    
This method is called when the KolodaView has no cards to display.
```swift
	func deckDidSelectCardAtIndex(deck: KolodaView, index: UInt)
```
This method is called when one of cards is tapped.
```swift
    func deckShouldApplyAppearAnimation(deck: KolodaView) -> Bool
```
This method is fired on reload, when any cards are displayed. If you return YES from the method, or don't implement it, the deck will apply appear animation.


Release Notes
----------------

Version 1.0

- Release version.

License
----------------

    The MIT License (MIT)

    Copyright © 2015 Yalantis

    Permission is hereby granted free of charge to any person obtaining a copy of this software and associated documentation files (the "Software") to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
    THE SOFTWARE.
