NOTE:: This is not a official loudmouth repo, so don't use this :)

ren compile : 
                                                                                
cmake  -G "NMake Makefiles" -DOPENSSL_INCLUDE_DIR=c:\OpenSSL\include\ -DSSL_EAY_DEBUG=c:\OpenSSL\lib\VC\ -DLM_COMPILATION=1  -DG_OS_WIN32=1 -DGLIBWIN32_INCLUDE_DIR=c:\telepathy-win32-build\include\glib-2.0 -DGLIB_RUNTIME=C:\telepathy-win32-build\bin\ -DGLIB_WIN_DEBUG=C:\telepathy-win32-build\lib\glib-2.0.lib ..                                            