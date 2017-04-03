I have used ZLSwipeavleView for executing this project.

Usage


ZLSwipeableView can be added to storyboard or instantiated programmatically:

ZLSwipeableView *swipeableView = [[ZLSwipeableView alloc] initWithFrame:self.view.frame];
[self.view addSubview:swipeableView];
A ZLSwipeableView must have an object that implements ZLSwipeableViewDataSource to act as a data source. ZLSwipeableView will prefetch three views in advance to animate them.

// required data source
self.swipeableView.dataSource = self;

#pragma mark - ZLSwipeableViewDataSource
- (UIView *)nextViewForSwipeableView:(ZLSwipeableView *)swipeableView {
  return [[UIView alloc] init];
}
The demo app includes examples of both creating views programmatically and loading views from Xib files that use Auto Layout.

A ZLSwipeableView can have an optional delegate to receive callback.

// optional delegate
self.swipeableView.delegate = self;

#pragma mark - ZLSwipeableViewDelegate
- (void)swipeableView:(ZLSwipeableView *)swipeableView
         didSwipeView:(UIView *)view
          inDirection:(ZLSwipeableViewDirection)direction {
    NSLog(@"did swipe in direction: %zd", direction);
}
- (void)swipeableView:(ZLSwipeableView *)swipeableView didCancelSwipe:(UIView *)view {
  NSLog(@"did cancel swipe");
}
- (void)swipeableView:(ZLSwipeableView *)swipeableView didStartSwipingView:(UIView *)view atLocation:(CGPoint)location {
    NSLog(@"did start swiping at location: x %f, y%f", location.x, location.y);
}
- (void)swipeableView:(ZLSwipeableView *)swipeableView swipingView:(UIView *)view atLocation:(CGPoint)location  translation:(CGPoint)translation {
	NSLog(@"swiping at location: x %f, y %f, translation: x %f, y %f", location.x, location.y, translation.x, translation.y);
}
- (void)swipeableView:(ZLSwipeableView *)swipeableView didEndSwipingView:(UIView *)view atLocation:(CGPoint)location {
    NSLog(@"did start swiping at location: x %f, y%f", location.x, location.y);
}
To swipe the top view programmatically:

[self.swipeableView swipeTopViewToLeft];
[self.swipeableView swipeTopViewToRight];
...
To discard all views and reload programmatically:

[self.swipeableView discardAllViews];
[self.swipeableView loadViewsIfNeeded];
