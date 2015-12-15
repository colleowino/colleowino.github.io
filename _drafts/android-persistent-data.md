---
layout:     post
title:      "saving data on android"
date:       2015-10-17 10:30:00 pm
tags: android java xml
categories: drafts
author:     "colleowino"
excerpt: "Android provides ways to save data on the device from user preferences,
internal storage and sqlite db."

---
- sqlite db
- user preferences
- 

Saving data to user preference. You can have  a settings page. Just make sure that the listener is properly set
with the PreferenceActivity through preferenceManager within the fragment.

      SharedPreferences prefs = PreferenceManager.getDefaultSharedPreferences(this);
      prefs.registerOnSharedPreferenceChangeListener(this);

then override the method

    public void onSharedPreferenceChanged(SharedPreferences sharedPreferences,
                                          String key) {
                                                  
      Preference pref = findPreference(key);
      pref.setSummary(sharedPreferences.getString(key, "nada"));
      
      }

To Display the value you use prefrenceManager again to get the prefernce and change its value.
within the onCreate() method call.

        Preference username =  getPreferenceManager().findPreference("prefUsername");
        username.setSummary(sharedPrefs.getString("prefUsername","if_value_wasNull"));
        
#### further reading 
- [android core documentation](http://developer.android.com/guide/topics/data/data-storage.html#filesInternal)

