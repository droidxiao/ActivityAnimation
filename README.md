# ActivityAnimation helper and ImageView transition With ViewPager
IGNORE APP NAME...
Just see WeChat IOS IOS IOS(not android) share moments,When u click friend's picture moments
or see gift below..
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-ActivityAnimation-green.svg?style=flat)](https://android-arsenal.com/details/1/2573)
# FINAL EFFECT
![EFFECT](./show.gif)

# REBOUND EFFECT
![REBOUND](./rebound.png)

#ImageView transition with ViewPager
 click view to see detail in other layout...

 Feature: Working on...

    1.original view: just like normal imageview but with zoom effect
    2.detail view:
    ① single click back to pre layout with shrink effect
    ② double click to zoom effect(*2.5)
    ③ more gesture see details code
    3.if u have more than one imageview can display with ViewPager
    random click original imageview,and scroll ViewPager to any position,
    than u press back key,or single click detail,u will see original view's
    position is the same as ViewPager‘s current position.

    4.load image from remote u can't click item until it finished

    5.ViewPager has rebound effect when edge of ViewPager is available..

About fragment listening onBackPressed
see this gist https://gist.github.com/brucetoo/f7c9bcabe2ce51610ccf

#ActivityAnimation Usage
```java
  Pre activity onCreate()..
  ActivityTransitionEnterHelper.with(this).fromView(fromView).imageUrl(imgUrl).start(Test.class);
  Sub activity onCreate()..
  transitionExitHelper = ActivityTransitionExitHelper.with(getIntent()).toView(mImageView).background(mBackgroudnView).start(savedInstanceState);
                      @Override
                      public void onBackPressed() {
                          transitionExitHelper.runExitAnimation(new Runnable() {
                              @Override
                              public void run() {
                                  finish();
                              }
                          });
                      }
                      @Override
                      public void finish() {
                          super.finish();
                          // override transitions to skip the standard window animations
                          overridePendingTransition(0, 0);
                      }
```

#TODO
 ~~1.add Loading State into viewPager~~

 2.maybe make this lib as a ***helper like ActivityTransitionEnterHelper

#THANKS
PhotoView from https://github.com/bm-x/PhotoView

Custom Activity Animations from https://www.youtube.com/watch?v=CPxkoe2MraA

## License

Copyright 2015 Bruce too

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

See [LICENSE](LICENSE) file for details.
