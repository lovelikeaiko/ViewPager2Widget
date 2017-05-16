# ViewPager2Widget
With these modifications in framework, you can use ViewPager in Widget.

All modifications are surrounded by comment like:
```Java
        //merged by HP started
        else if ((v != null) && (v instanceof ViewPager)){
            
            ViewPager vp = (ViewPager) v;
            
            //Log.i(TAG, "viewDataChanged, vp.getAdapter() == null?" + (vp.getAdapter() == null));
            
            if(vp.getAdapter() != null){
                vp.getAdapter().notifyDataSetChanged();
            }  else if (vp.getAdapter() == null && vp instanceof RemoteAdapterConnectionCallback) {
                // If the adapter is null, it may mean that the RemoteViewsAapter has not yet
                // connected to its associated service, and hence the adapter hasn't been set.
                // In this case, we need to defer the notify call until it has been set.
                ((RemoteAdapterConnectionCallback) vp).deferNotifyDataSetChanged();
            }
            
        }
        //merged by HP ended 
```
You can just search key words "HP" to find where are these modifications.
