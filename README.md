This is a fork of https://code.qt.io/cgit/qt-labs/qtpdf.git with some modifications.

It is released under the same license (GPL3 + LGPL3)

In order to build this module, the following patch for the pdfium submodule might be required

```
diff --git a/third_party/lcms2-2.6/include/lcms2.h b/third_party/lcms2-2.6/include/lcms2.h
index 8595f7020..8dd053702 100644
--- a/third_party/lcms2-2.6/include/lcms2.h
+++ b/third_party/lcms2-2.6/include/lcms2.h
@@ -1234,13 +1234,13 @@ CMSAPI cmsStageSignature CMSEXPORT cmsStageType(const cmsStage* mpe);
 CMSAPI void*             CMSEXPORT cmsStageData(const cmsStage* mpe);
 
 // Sampling
-typedef cmsInt32Number (* cmsSAMPLER16)   (register const cmsUInt16Number In[],
-                                            register cmsUInt16Number Out[],
-                                            register void * Cargo);
+typedef cmsInt32Number (* cmsSAMPLER16)   (const cmsUInt16Number In[],
+                                            cmsUInt16Number Out[],
+                                            void * Cargo);
 
-typedef cmsInt32Number (* cmsSAMPLERFLOAT)(register const cmsFloat32Number In[],
-                                            register cmsFloat32Number Out[],
-                                            register void * Cargo);
+typedef cmsInt32Number (* cmsSAMPLERFLOAT)(const cmsFloat32Number In[],
+                                            cmsFloat32Number Out[],
+                                            void * Cargo);
 
 // Use this flag to prevent changes being written to destination
 #define SAMPLER_INSPECT     0x01000000
```
