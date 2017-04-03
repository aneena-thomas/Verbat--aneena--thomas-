{\rtf1\ansi\ansicpg1252\cocoartf1404\cocoasubrtf470
{\fonttbl\f0\froman\fcharset0 Times-Roman;}
{\colortbl;\red255\green255\blue255;\red27\green31\blue34;\red10\green77\blue204;\red148\green6\blue75;
\red244\green246\blue249;\red14\green114\blue164;\red101\green71\blue146;\red132\green134\blue132;\red38\green38\blue38;
\red19\green36\blue126;}
\paperw11900\paperh16840\margl1440\margr1440\vieww10800\viewh8400\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs26 \cf0 I have used ZLSwipeableView for this project.\
\pard\pardeftab720\sl440\sa320\partightenfactor0

\b \cf2 \expnd0\expndtw0\kerning0
Usage\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 Check out the {\field{\*\fldinst{HYPERLINK "https://github.com/zhxnlai/ZLSwipeableViewSwift/archive/master.zip"}}{\fldrslt \cf3 demo app}} for an example. It contains the following demos: Default, Custom Animation, Custom Swipe, Allowed Direction, History, Previous View, Should Swipe and Always Swipe.\
\pard\pardeftab720\sl300\partightenfactor0

\b \cf3 \
\pard\pardeftab720\sl360\sa320\partightenfactor0
\cf2 Instantiation\
\pard\pardeftab720\sl320\sa320\partightenfactor0

\b0 \cf2  \cf0 \kerning1\expnd0\expndtw0 ZLSwipeableView  \cf2 \expnd0\expndtw0\kerning0
can be added to storyboard or instantiated programmatically:\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 \cb5 var\cf2  swipeableView \cf4 =\cf2  \cf6 ZLSwipeableView\cf2 (\cf6 frame\cf2 : \cf6 CGRect\cf2 (\cf6 x\cf2 : \cf6 0\cf2 , \cf6 y\cf2 : \cf6 0\cf2 , \cf6 width\cf2 : \cf6 300\cf2 , \cf6 height\cf2 : \cf6 500\cf2 ))\
view.\cf6 addSubview\cf2 (swipeableView)\
\pard\pardeftab720\sl300\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl360\sa320\partightenfactor0
\cf2 Adding View\
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\b0 \cf0 \kerning1\expnd0\expndtw0 ZLSwipeableView\cf2 \expnd0\expndtw0\kerning0
 supports both adding views to the front and to the back.\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 \cb5 public\cf2  \cf4 var\cf2  numberOfActiveView \cf4 =\cf2  \cf6 UInt\cf2 (\cf6 4\cf2 )\
\cf4 public\cf2  \cf4 var\cf2  nextView\cf4 :\cf2  (() \cf4 ->\cf2  UIView\cf4 ?\cf2 )\cf4 ?\cf2 \
\cf4 public\cf2  \cf4 var\cf2  previousView\cf4 :\cf2  (() \cf4 ->\cf2  UIView\cf4 ?\cf2 )\cf4 ?\cf2 \
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 Adding views to the back\
nextView
\b0  a closure that returns an UIView, works with loadViews and numberOfActiveView. It acts as the data source. After defining it, ZLSwipeableView will call loadViews which will invoke nextView numberOfActiveView times and insert them in the back.loadViews will also be called each time a view is swiped.\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 \cb5 public\cf2  \cf4 func\cf2  \cf7 loadViews\cf2 ()\
\pard\pardeftab720\sl380\partightenfactor0
\cf8 // Usage:\cf2 \
swipeableView.\cf9 numberOfActiveView\cf2  \cf4 =\cf2  \cf6 3\cf2 \
swipeableView.\cf9 nextView\cf2  \cf4 =\cf2  \{\
  \cf4 return\cf2  \cf6 UIView\cf2 ()\
\}\
swipeableView.\cf6 loadViews\cf2 () \cf8 // optional, automatically call after nextView is set\cf2 \
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 Adding views to the front\
\pard\pardeftab720\sl320\sa320\partightenfactor0

\b0 \cf2 previousView works with rewind, which inserts a view in the front and positions it at the center with animation. Note that rewind calls previousView only when history is empty, otherwise it returns the most recently swiped view. Please try out the {\field{\*\fldinst{HYPERLINK "https://github.com/zhxnlai/ZLSwipeableViewSwift/blob/master/README.md#rewind"}}{\fldrslt \cf3 Previous View}} example for more information.\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 \cb5 public\cf2  \cf4 func\cf2  \cf7 rewind\cf2 ()\
\pard\pardeftab720\sl380\partightenfactor0
\cf8 // Usage:\cf2 \
swipeableView.\cf9 previousView\cf2  \cf4 =\cf2  \{\
  \cf4 return\cf2  \cf6 UIView\cf2 ()\
\}\
swipeableView.\cf6 rewind\cf2 ()\
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 Interface Builder\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 If you need to work with Interface Builder, the demo app includes examples of both creating views programmatically and loading views from Xib files that {\field{\*\fldinst{HYPERLINK "https://github.com/zhxnlai/ZLSwipeableView/issues/9"}}{\fldrslt \cf3 use Auto Layout}}.\
\pard\pardeftab720\sl300\partightenfactor0

\b \cf3 \
\pard\pardeftab720\sl360\sa320\partightenfactor0
\cf2 Removing Views\
\pard\pardeftab720\sl320\partightenfactor0
\cf3 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 Swiping programmatically\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 The user can swipe views in the allowed directions. This can also happen programmatically.\
You can swipe the top view programmatically in one of the predefined directions or with point and direction in the view's coordinate.\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 \cb5 public\cf2  \cf4 func\cf2  \cf7 swipeTopView\cf2 (\cf7 inDirection\cf2  \cf9 direction\cf2 : Direction)\
\pard\pardeftab720\sl380\partightenfactor0
\cf8 // Usage:\cf2 \
swipeableView.\cf6 swipeTopView\cf2 (\cf6 inDirection\cf2 : .\cf9 Left\cf2 )\
swipeableView.\cf6 swipeTopView\cf2 (\cf6 inDirection\cf2 : .\cf9 Up\cf2 )\
swipeableView.\cf6 swipeTopView\cf2 (\cf6 inDirection\cf2 : .\cf9 Right\cf2 )\
swipeableView.\cf6 swipeTopView\cf2 (\cf6 inDirection\cf2 : .\cf9 Down\cf2 )\
\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 public\cf2  \cf4 func\cf2  \cf7 swipeTopView\cf2 (\cf7 fromPoint\cf2  \cf9 location\cf2 : CGPoint, \cf7 inDirection\cf2  \cf9 directionVector\cf2 : CGVector)\
\pard\pardeftab720\sl380\partightenfactor0
\cf8 // Usage:\cf2 \
swipeableView.\cf6 swipeTopView\cf2 (\cf6 fromPoint\cf2 : \cf6 CGPoint\cf2 (\cf6 x\cf2 : \cf6 100\cf2 , \cf6 y\cf2 : \cf6 30\cf2 ), \cf6 inDirection\cf2 : \cf6 CGVector\cf2 (\cf6 dx\cf2 : \cf6 100\cf2 , \cf6 dy\cf2 : \cf6 -800\cf2 ))\
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 Rewinding\
\pard\pardeftab720\sl320\sa320\partightenfactor0

\b0 \cf2 ZLSwipeableView keeps a history of swiped views. They can be retrieved by calling rewind.\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 \cb5 public\cf2  \cf4 var\cf2  history \cf4 =\cf2  [UIView]()\
\cf4 public\cf2  \cf4 var\cf2  numberOfHistoryItem \cf4 =\cf2  \cf6 UInt\cf2 (\cf6 10\cf2 )\
\
\cf4 public\cf2  \cf4 func\cf2  \cf7 rewind\cf2 ()\
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 Removing all views\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 To discard all views and reload programmatically (discarded views cannot by rewinded):\
\pard\pardeftab720\sl380\partightenfactor0
\cf2 \cb5 swipeableView.\cf6 discardViews\cf2 ()\
swipeableView.\cf6 loadViews\cf2 ()\
\pard\pardeftab720\sl300\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl360\sa320\partightenfactor0
\cf2 Delegate\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 Here is a list of callbacks you can listen to:\
\pard\pardeftab720\sl380\partightenfactor0
\cf2 \cb5 swipeableView.\cf9 didStart\cf2  \cf4 =\cf2  \{view, location \cf4 in\cf2 \
    \cf6 print\cf2 (\cf10 "Did start swiping view at location: \\(\cf9 location\cf10 )"\cf2 )\
\}\
swipeableView.\cf9 swiping\cf2  \cf4 =\cf2  \{view, location, translation \cf4 in\cf2 \
    \cf6 print\cf2 (\cf10 "Swiping at view location: \\(\cf9 location\cf10 ) translation: \\(\cf9 translation\cf10 )"\cf2 )\
\}\
swipeableView.\cf9 didEnd\cf2  \cf4 =\cf2  \{view, location \cf4 in\cf2 \
    \cf6 print\cf2 (\cf10 "Did end swiping view at location: \\(\cf9 location\cf10 )"\cf2 )\
\}\
swipeableView.\cf9 didSwipe\cf2  \cf4 =\cf2  \{view, direction, vector \cf4 in\cf2 \
    \cf6 print\cf2 (\cf10 "Did swipe view in direction: \\(\cf9 direction\cf10 ), vector: \\(\cf9 vector\cf10 )"\cf2 )\
\}\
swipeableView.\cf9 didCancel\cf2  \cf4 =\cf2  \{view \cf4 in\cf2 \
    \cf6 print\cf2 (\cf10 "Did cancel swiping view"\cf2 )\
\}\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b \cf2 \cb1 Customization\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 Here is a list of customizable behaviors:\
\pard\pardeftab720\sl380\partightenfactor0
\cf4 \cb5 public\cf2  \cf4 var\cf2  animateView \cf4 =\cf2  ZLSwipeableView.\cf6 defaultAnimateViewHandler\cf2 ()\
\cf4 public\cf2  \cf4 var\cf2  interpretDirection \cf4 =\cf2  ZLSwipeableView.\cf6 defaultInterpretDirectionHandler\cf2 ()\
\cf4 public\cf2  \cf4 var\cf2  shouldSwipeView \cf4 =\cf2  ZLSwipeableView.\cf6 defaultShouldSwipeViewHandler\cf2 ()\
\cf4 public\cf2  \cf4 var\cf2  minTranslationInPercent \cf4 =\cf2  \cf6 CGFloat\cf2 (\cf6 0.25\cf2 )\
\cf4 public\cf2  \cf4 var\cf2  minVelocityInPointPerSecond \cf4 =\cf2  \cf6 CGFloat\cf2 (\cf6 750\cf2 )\
\cf4 public\cf2  \cf4 var\cf2  allowedDirection \cf4 =\cf2  Direction.\cf9 Horizontal\cf2 \
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \cb1 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 interpretDirection\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 You can change how the direction gets interpreted by overriding the interpretDirection property. Take a look at the {\field{\*\fldinst{HYPERLINK "https://github.com/zhxnlai/ZLSwipeableViewSwift/blob/master/README.md#custom-swipe"}}{\fldrslt \cf3 Custom Swipe}} example for details.\
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 animateView\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 You can create custom animation by overriding the animateView property. Take a look at the {\field{\*\fldinst{HYPERLINK "https://github.com/zhxnlai/ZLSwipeableViewSwift/blob/master/README.md#custom-animation"}}{\fldrslt \cf3 Custom Animation}} example for details.\
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 Should Swipe\
\pard\pardeftab720\sl320\sa320\partightenfactor0

\b0 \cf2 shouldSwipeView, minTranslationInPercent and minVelocityInPointPerSecond determines whether a view should be swiped or not. Please see the Should Swipe example for details.\
\pard\pardeftab720\sl320\partightenfactor0

\b \cf3 \
\pard\pardeftab720\sl400\sa320\partightenfactor0
\cf2 allowedDirection\
\pard\pardeftab720\sl360\sa320\partightenfactor0

\b0 \cf2 The allowedDirection property limits the directions in which the user is allowed to swipe. Please see the {\field{\*\fldinst{HYPERLINK "https://github.com/zhxnlai/ZLSwipeableViewSwift/blob/master/README.md#custom-direction"}}{\fldrslt \cf3 Custom Direction}} example for details.\
\pard\pardeftab720\sl380\partightenfactor0
\cf2 \cb5 swipeableView.\cf9 allowedDirection\cf2  \cf4 =\cf2  .\cf9 Left\cf2  \cf4 |\cf2  .\cf9 Up\cf2 \
swipeableView.\cf9 allowedDirection\cf2  \cf4 =\cf2  .\cf9 All\cf2 \
\pard\pardeftab720\sl300\partightenfactor0

\b \cf3 \cb1 \
}