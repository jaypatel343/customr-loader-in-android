# Create Method in your activity

    public static Dialog createCustomLoader(Context mContext, boolean isCancelable) {
        final Dialog dialog = new Dialog(mContext);
        dialog.requestWindowFeature(Window.FEATURE_NO_TITLE);
        dialog.getWindow().setBackgroundDrawable(new ColorDrawable(Color.TRANSPARENT));
        dialog.setCancelable(isCancelable);
        dialog.setContentView(R.layout.custom_loader);

        WindowManager.LayoutParams lp = new WindowManager.LayoutParams();
        Window window = dialog.getWindow();
        lp.copyFrom(window.getAttributes());
        lp.width = WindowManager.LayoutParams.MATCH_PARENT;
        lp.height = WindowManager.LayoutParams.WRAP_CONTENT;
        window.setAttributes(lp);
        return dialog;
    }

#create custome_loader.xml file and write this script

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#00FFFFFF"
    android:gravity="center"
    android:orientation="vertical">

    <LinearLayout
        android:layout_width="@dimen/_40sdp"
        android:layout_height="@dimen/_40sdp"
        android:orientation="vertical">

        <ProgressBar
            android:id="@+id/progressBar"
            style="@style/Base.Widget.AppCompat.ProgressBar"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_gravity="center"
            android:layout_margin="@dimen/_6sdp"
            android:indeterminateTint="@color/bgBottomNavigation"
            android:progress="0" />


    </LinearLayout>

</LinearLayout>

# write this code in oncreate method

dialog = CommonUtils.createCustomLoader(LoginActivity.this, false);

# call below method for show the loaded
dialog.show();

# call below method for disable the loaded
dialog.dismiss()
