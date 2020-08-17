# asan_mfc_sdi_mdi_crash
This is reproduction of MFC SDI and MDI application crash in WinMain in ASAN in debug mode

This repo is for the [bug report](https://developercommunity.visualstudio.com/content/problem/1152487/mfc-sdi-and-mdi-application-crash-in-winmain-in-as.html).

MFCApplication4 is SDI and MFCApplication5 is MDI. Both are auto-generated from AppWizard without custom code.

* If the MFC application is dialog based, the crash does not happen.
* If the MFC application (SDI or MDI) is in release build, the crash does not happen.

The crash occurs on line 25 of appmodul.cpp. See below:

```
return AfxWinMain(hInstance, hPrevInstance, lpCmdLine, nCmdShow);
```

The error in x86 is 

```
HEAP[MFCApplication5.exe]: Invalid address specified to RtlValidateHeap( 00830000, 03D039E0 )
```