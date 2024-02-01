# 3D visualization of fMRI img

### 参考文献

[NCBI - WWW Error Blocked Diagnostic](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4648228/)

### 下载工具

1. ITK-SNAP 
    
    [ITK-SNAP Home](http://www.itksnap.org/pmwiki/pmwiki.php)
    
2. ParaView
    
    [Download ParaView](https://www.paraview.org/download/)
    
3. Sample data: 
    
    [NCBI - WWW Error Blocked Diagnostic](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4648228/)
    
    ![CleanShot 2023-10-06 at 19.01.15@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_19.01.152x.png)
    

### 操作流程

1. 准备图像文件（也可以选择用sample data中的文件试用）
    1. 对自己已计算好的statmap.nii文件进行height threshold和cluster的操作（假定输出文件名：statmapThresh.nii）；
    2. 对anatomical.nii文件执行同样的height threshold，不需要执行cluster（假定输出文件名：glassbrain.nii）
2. 用ITK-SNAP将NIfTI文件转换为VTK的格式
    1. 下载并打开**ITK-SNAP**
    2. 将两个文件分别各自作为**main image**和**segmentation image**导入ITK-SNAP中：
        1. 拖动statmapThresh.nii到ITK-SNAP界面（第一次拖入会自动作为main image）
            
            ![CleanShot 2023-10-06 at 21.07.33@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.07.332x.png)
            
        2. 再次拖动statmapThresh.nii到ITK-SNAP界面，在出现的弹窗中选择”**Load as Segmentation**”
            
            ![CleanShot 2023-10-06 at 21.08.22@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.08.222x.png)
            
            ![CleanShot 2023-10-06 at 21.16.38@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.16.382x.png)
            
    3. 保存文件：点击菜单栏的“**Segmentation**”, 依次选择 “**Export as surface mesh”**，”**Export meshes for all labels as a single scene**”，然后为文件命名（例，**statmapThresh.vtk**），该VTK文件即保存在与原文件相同的位置。
    4. 对**glassbrain.nii**执行以上相同的操作，并保存（**glassbrain.vtk**）
3. 在ParaView中进行3D可视化（也可以选择使用sample data中的文件👇）
    
    ![CleanShot 2023-10-06 at 22.01.08@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_22.01.082x.png)
    
    1. 将两个VTK文件都导入ParaView中，并放在一个builtin下，并把左边的两个眼睛图标点开，此时获得了3D脑图
        
        ![CleanShot 2023-10-06 at 21.26.29@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.26.292x.png)
        
    2. 调整ParaView的设置，使其符合个人的需求
        1. 在**builtin**下选中**glassbrain.vtk**
            
            ![CleanShot 2023-10-06 at 21.33.12@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.33.122x.png)
            
            1. 通过左侧**opacity**将**glassbrain**设置为半透明
            2. 更改右侧**color map**选择心仪的颜色
            3. 隐藏**color legend**（更改后⬇️
            
            ![CleanShot 2023-10-06 at 21.36.17@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.36.172x.png)
            
        2. 在builtin下选择statmapThresh.vtk
            
            ![CleanShot 2023-10-06 at 21.49.35@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.49.352x.png)
            
            1. 左侧选择“**Use separate color map**”，可以选择与glassbrain不同的颜色
            2. 右侧更改**color map**
        3. 颜色、背景自定义
            
            ![CleanShot 2023-10-06 at 21.56.49@2x.png](3D%20visualization%20of%20fMRI%20img%2073a3697a4ad74a0e807bdf22c1a6cfc5/CleanShot_2023-10-06_at_21.56.492x.png)
            
            1. 左侧取消勾选“**Use color palette for background**”，点击下方的“**Background”**选择其他颜色
            2. 右侧选择 “**Use below range color**”，在 “Below Range Color”中选择脑区的颜色
            3. 鼠标点击中间的大脑，滑动调整视图的角度
        4. 保存文件
            1. 保存为**pvsm**文件：菜单栏选择“**File**” - “**Save state**”，输入文件名并选择保存地
            2. 保存为截图：菜单栏选择“**File**” - “**Save screenshot**”

### 用adobe illustrator作图

优点：

1. 可转为矢量图
2. 可去除背景

详细参考：

[How to convert the inserted picture into vector illustration?](https://www.notion.so/How-to-convert-the-inserted-picture-into-vector-illustration-974600d35a0b4902832232a06e5bd7b8?pvs=21)