# Test with Textures

I compared results I managed to obtain with OpenCV(4.7.0) (with cv.INPAINT_NS and cv.INPAINT_TELEA), for simple textures with small inpaint regions, results from <b>MagicInpainter 3.0</b> are much better:

| <img src="brick1/brick-texture-png-23887_red2.jpg" width="200px"/> |  <img src="brick1/brick-texture-png-23887_inpainted_MI.jpg" width="200px"/> | <img src="brick1/brick-texture-png-23887_inpainted_cv2.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Texture, 400x400</b>* | *<b>MagicInpainter 3.0, R15</b>* | *<b>OpenCV, R15,NS</b>* |


I also compared inpaint of texture images with some of the AI assisted applications that I found on the net. For small inpaint area, Inpaint app (from https://theinpaint.com) weren’t able to cope very well, but SnapEdit (https://snapedit.app) and ClipDrop (https://cleanup.pictures) showed good results (both are claiming to use AI). Still if we look closely will see that these AI apps have made some minor errors.


| <img src="cloth1/cloth1_red1.jpg" width="200px"/> |  <img src="cloth1/cloth1_inpainted_MI_R32_pass2.jpg" width="200px"/> | <img src="cloth1/cloth1_inpainted_cv2_NS_r20.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Texture, 308x305</b>* | *<b>MagicInpainter 3.0, R32</b>* | *<b>OpenCV, R 20,NS</b>* |
| <img src="cloth1/cloth1_inpainted_inpaint.jpg" width="200px"/> |  <img src="cloth1/snapedit_1674684435592.jpg" width="200px"/> | <img src="cloth1/cloth1_red1_cleanup1.jpg" width="200px"/> | 
| *<b>InpaintApp</b>* | *<b>SnapEdit</b>* | *<b>CleanUp</b>* |

| <img src="textur9/textur9_22.JPG" width="200px"/> |  <img src="textur9/textur9_22_MI_r5.jpg" width="200px"/> | <img src="textur9/snapedit_1674693014145.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Texture, 200x200</b>* | *<b>MagicInpainter 3.0, R5</b>* | *<b>SnapEdit</b>* |


| <img src="text042/text042_red1.jpg" width="200px"/> |  <img src="text042/text042_red1_inpainted_MI_r5.jpg" width="200px"/> | <img src="text042/text042_red1_inpainted_cleanup.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Texture, 178x178</b>* | *<b>MagicInpainter 3.0, R5</b>* | *<b>CleanUp</b>* |


Problems of AI apps with textures becomes more obvious when inpaint region becomes bigger and placed at the edges, while <b>MagicInpainter 3.0</b> works fine even in some very extreme cases:


| <img src="cloth3/wildtextures_small_filled1.jpg" width="200px"/> |  <img src="cloth3/wildtextures_small_filled1_MI_r15.jpg" width="200px"/> | <img src="cloth3/wildtextures_small_filled1_cleanup.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Texture, 640x640</b>* | *<b>MagicInpainter 3.0, R15</b>* | *<b>CleanUp</b>* |

| <img src="cloth6/cloth-violet-green_small_filled.jpg" width="200px"/> |  <img src="cloth6/cloth-violet-green_small_filled_MI_R15.jpg" width="200px"/> | <img src="cloth6/cloth-violet-green_small_filled_snapedit.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Texture, 400x400</b>* | *<b>MagicInpainter 3.0, R15</b>* | *<b>SnapEdit</b>* |

| <img src="cloth4/table-cloth-blue_small_filled.jpg" width="200px"/> |  <img src="cloth4/table-cloth-blue_small_filled_inpainted_MI_r15.jpg" width="200px"/> | <img src="cloth4/table-cloth-blue_small_filled_snap_edit.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Texture, 400x400</b>* | *<b>MagicInpainter 3.0, R15</b>* | *<b>SnapEdit</b>* |


Some of the recent AI libraries, like the famous HuggingFace Diffusers trained on almost <b>6 billlion images</b> (see: https://huggingface.co/runwayml/stable-diffusion-inpainting) also have quality issues. For example here is the best I could to produce with removing the dog and using the COLAB example from the link:

| <img src="dog/dog.jpg" width="200px"/> |  <img src="dog/dog_MI_many_passes_r45.jpg" width="200px"/> | <img src="dog/dog_inpaint.jpg" width="200px"/> | 
|---|---|---| 
| *<b>Original Image, 512x412</b>* | *<b>MagicInpainter 3.0, R45-50</b>* | *<b>HuggingFace Diffusers</b>* |



These tests shows that MagicInpainter 3.0 preserves precisely the texture patters without penalty from the inpaint area size and algorithm can be used for textures generation. While AI darkens or lighten the deeper inpaint area and in the third example is unable to reproduce patterns.
<p>
My tests show that AI apps are optimized more for real-life photos and are not precise enough for inpaint of vector textures. The reason for this is the heuristics nature of the neural networks, they make errors during the initial inpaint and errors are later incremented while go deeper in the inpaint region. For real-life photos these errors are not usually noticeble because there is no strict repetition of the patterns.  
</p>
