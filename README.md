1.Rotation Matrix (Y-axis): 自行完成
2.Matrix4::makeRotX(float a): 自行完成
前兩項都是上次作業的東西，直接複製貼上即可

3.Model Transformation (Model Matrix): 自行完成
<img width="1082" height="970" alt="image" src="https://github.com/user-attachments/assets/cf4d4e2d-9279-4847-a8f3-ef74917d2237" />
使用老師教過的方法，先將眼睛的位置移動到座標軸原點，再依序分別旋轉y,z,x軸，最後再處理縮放，就像是對worldToLocal的相反操作而已

4.Camera Transformation (View Matrix): 自行完成
<img width="1088" height="1082" alt="image" src="https://github.com/user-attachments/assets/37e9efd0-df7b-4134-8a6f-532fdf4c3598" />
輸入的pos是鏡頭位置，lookat是鏡頭對準對準的位置，也就是COI，除此之外程式內建topVector = (0,1,0)。
因此只要使用pos和lookat算出view向量，再和top作外積得到right向量，再用view和right作外積的到up向量。然後將right,up,view做成GRM。
接者將鏡頭移到原點後，用GRM對他做旋轉就完成了

5.Perspective Rendering: 自行完成
<img width="1306" height="548" alt="image" src="https://github.com/user-attachments/assets/20539d5e-41a7-49a5-8027-64f725148476" />
<img width="1660" height="668" alt="image" src="https://github.com/user-attachments/assets/c5495810-60db-4d9b-a17b-e3c46b3a7dd2" />
使用老師教的Perspective Projection Matrix，其中w,h分別是鏡頭寬度與長度,n代表Hither Plane，f代表Yon Plane。
tan則是使用tan(GH_FOV)取得，命名為t，將各個參數分別放進矩陣即可得出

6.Depth Buffer: 自行完成
<img width="2094" height="918" alt="image" src="https://github.com/user-attachments/assets/0e4c0200-acaf-4795-baa0-1d5c1e4fe8d4" />
<img width="2092" height="866" alt="image" src="https://github.com/user-attachments/assets/0bf6cb5c-548e-4db7-893b-16e8b77436c3" />
使用老師教過的平面方程式，將輸入的三個頂點v1,v2,v3求出兩向量，v1v2,v1v3，分別命名為e1,e2，再以e1與e2作外積，求得法向量N。
此法向量的三維分別為nx,ny,nz。再以v1的三維作為xi,yi,zi，再與輸入的x,y,z帶入方程式，求得最後的z。

7.Camera Control: 自行完成
這個部分比較單純，讓電腦偵測按鍵w,s,a,d,e,q，讓鏡頭分別移動依照上,下,左,右,前,後的方向移動，並且可以調整速度

8.Backculling: 用ChatGPT協助完成
Back Face Culling 是利用三角形的頂點順序判斷其是否面向相機。對於背向相機的三角形，直接忽略不進行繪製，以減少不必要的運算並提升渲染效率。
本作業透過計算投影後兩條邊的叉積方向來判斷三角形的正反面。


螢幕截圖:
<img width="1874" height="1072" alt="image" src="https://github.com/user-attachments/assets/517c2288-f1a6-40e9-b369-f57275373dd1" />
