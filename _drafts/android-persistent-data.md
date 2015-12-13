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
with the PreferenceActivity through preferenceManager.

      SharedPreferences prefs = PreferenceManager.getDefaultSharedPreferences(this);
      prefs.registerOnSharedPreferenceChangeListener(this);

then override the method

    public void onSharedPreferenceChanged(SharedPreferences sharedPreferences,
                                          String key) {

#### further reading 
- [android core documentation](http://developer.android.com/guide/topics/data/data-storage.html#filesInternal)

