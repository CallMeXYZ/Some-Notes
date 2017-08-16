- setTextSize(int unit, int size)TypedValue.COMPLEX_UNIT_PX : PixelsTypedValue.COMPLEX_UNIT_SP :Scaled PixelsTypedValue.COMPLEX_UNIT_DIP : Device Independent Pixels
- 但是textview中getTextSize返回值是以像素(px)为单位的，而setTextSize()是以sp为单位的
- 异步加载里不能settext!
- alrmmanagement  记得加userpermission
- 判断密码两次输入是否相等 trim();
-  setUserVisibleHint is only accessible in FragmentPageAdapter
- scrollview 里嵌套listview gridview 只显示单行
- setImageResource是同步的，资源图片的读取和解码都是在主线程中进行的。setImageDrawable是异步的。加载速度的区别。setImageResource要快于setImageDrawable和setImageBitmap.
- found carriage return (\r) without corresponding newline (\n)  ctrl A+X+V+S
- listview adapter visible  set visible 或者gone必须！
- softinput manifext resize
- cast (youractivity)getActivity()
- inflater(,,false) the specific child already has a parent
- translate fromXDelta 100% 与100%p 
-  FragmentPagerAdapter getFragment private String getFragmentTag(int fragmentPosition) {
		return "android:switcher:" + R.id.pager + ":" + fragmentPosition;
	}
- addheadview setonitemtclick pisition-1 or parent.getItemAtPosition(position),onclick不会错；
- Math.round(TypedValue.applyDimension(TypedValue.COMPLEX_UNIT_DIP, 210, context.getResources().getDisplayMetrics()));
- view.getloctiononscreen
- getChildFragmentManager!!nested fragment
- transaction.addToBackStack after u remove or replace a fragment so that user can navigate back
- context.getFileDir() or gerCacheDir()
- Alternatively, you can call openFileOutput() to get a FileOutputStream that writes to a file in your internal directory.
- When the user uninstalls your app, the Android system deletes the following:
   All files you saved on internal storage
   All files you saved on external storage using getExternalFilesDir().
- queryIntentActivities() before send an implicit intent
- textview.getpaint().setflags(Paint.UNDERLINE_TEXT_FLAGS)
- enabled and clickeable if clickable false then long click still fuctions
- dialog u must setOnKeyListener rather than override onKeyDown
- onkeydown cannot listene back key ,u can use onbackpressed  LOL
- setresult should before super.onBackPressed in onBackPressed
- API 18 android - 3 Bluetooth low energy

- seekbar progressdrawable layer-list clip maxheight minheight
- screen size getActivity().getWindowManager().getDefaultDisplay().getSize(new Point());
-  start an activity outside an activity should set FLAG_ACTIVITY_NEW_TASK
-  android - 0杀死应用进程后并不会杀死应用内的闹钟
- PowerManager.PARTIAL_WAKE_LOCK cannot wake up the screen use SCREEN_DIM_WAKE_LOCK or SCREEN_BRIGHT_WAKE_LOCK; But the best choice is to user PATIEAL_WAKE_LOCK to wake up the screen then in the activity set WindowManger.LayoutParams.FlAG_KEEP_SCREEN_ON
- 以后 start Intent(String) 必须加上setPackageName();
- parcel marshall和unmarshall前都要加上setDataPosition;
- Calendar getDayOfWeek 妙法 (getDayOfweek+5)%7
- contentProvider insert时 	ContentValues mValues = new ContentValues(values);but why
- when u comes with View1 cannot be cast into View2,u may need to delete the R file and recreate it;
-  dialog alginleft problem :getWindow().setlayout(match_parent,wrap_content);  wrong
- seekbar thumb if set offset=0 then u cannot get the center position of thumb
-  如int i = 1000000; long j = 1000+i*100000000000; !!!bug,i*100000000000超过i最大值会显示为最大值
- button with image and text
```
android:drawableLeft="@drawable/icon_uploading_gray"
android:drawablePadding="10dp"
android:gravity="left|center_vertical"
```
-  return type="json" timestamp??? @JSON(format = "yyyy-MM-dd HH:mm:ss")
- do things like setResult() before super.onbackPressed(); or you will get default resultcold(0)
- preference.editor.commit后立刻离开activity可能会失败，毕竟读写需要时间
- data/data/pachage need phone root to show
- visibiliy = gone 以及 无法显示（parent 太小） 很可能得到的getheight 和getwidth 都是 0 ；
- view- getViewTreeObserver().addOnGlobalLayoutListener getheight before show
- relativelayout 里的 imageview ，在设置relativeLayout 宽高后后zoom效果
- service intent must be explicit. just setPackage both start and stop
- android weight 在match parent 和wrap_content 时的不同
- android bugs nested fragment
- edittext 对于小数有可能以小数点开始或者结尾，注意判断
- editext onEditorAction
- using dialogfragment other than dialog
-  never and never put a scrollable view inside another , you foolish fucking fish!
- drawlayout.setlockmode
- recyclerview StaggeredGridLayoutManager
- app:layout_anchor app:layout_anchorGravity for floatactionbutton
- arraylist<>(size) the size doestn't mean this list's size but its max size u fool!
- navigationView.getMenu().getItem(0).setChecked(true);
- tinmanager
- d better not  to usr list = list2; rather  list.clear(); list.addAll()
- custom style save in style.xml
-  Relative width wrap_content 里的 view width match_parent 似乎无效 换成lienearLayout 成功 难道是linearlayoutmanager 的作用? 
- get drawble from res then setColorFilter PorterDuff 
- list preference only support string array remember to convert after got 
- listpreference forbid dialog  overide showDialog
- after setSupportActoolbar the toolbar's setTitle doesnt work,use getSupportActionBar.setTitle instead. But when u have a navigationDrawable it seems still work
- settheme should called before setContentView so when after changed ur activity in back state may need to be recreated
- settheme must call before supe.create or some attr such as windowbackground wont work 145
-  when use weight be carefull of odp wrap_content and match_parent
- dialogfragment match_parent `setStyle(DialogFragment.STYLE_NO_TITLE,android.R.style.Theme_Holo_Light_Dialog_NoActionBar_MinWidth)`
- customview extends viewgroup,addview(child) in onmeasure and onLayout calculate and set child's size call:getChildAt(),child.onMeasure ,child.onLayout
- isInEditMode()
- cardview cardBackgroundColor should be set when using whole context theme background color
- sometimes need parcel to store sth maybe u can try bundle
- setBackGround(null) maybe cause resize problem
-  注释换行 <p/>
- RelativeLayout.LayoutParams addRule(RelativeLayout.。。)
- android studio ALT+TAB perfect!!!!
