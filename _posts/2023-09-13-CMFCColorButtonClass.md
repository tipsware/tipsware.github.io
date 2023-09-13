---
layout: post
title: CMFCColorBar Class
subtitle: This is a CMFCColorBar Class example
categories: MFC
banner:
  image: /assets/images/color_bar1.gif
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: mfc cmfccolorbutton
top: 1
---

## CMFColorButton

CMFColorButton, which is provided in the form of a combo box when selecting a color, is effective when there is not enough UI space, but it has the disadvantage of increasing the number of clicks for color selection. And CMFColorDialog can be selected while looking at many colors at once, but it's inevitably uncomfortable if you have to choose repeatedly because you have to work with a dialog box every time. Therefore, the class that allows CMFColorButton to be used in the form of a list box is the CMFColorBar class. This class allows you to list and select colors as shown below. This class also provides a 'select another color' function immediately, so you don't need to add a separate CMFColorDialog usage code when you need additional colors.

![Crepe](/assets/images/color_bar1.gif)

Because this control cannot be selected in the Resource Editor, you must create it by giving it your own coordinates and IDs. For example, if you want to create this control with the control ID 2301 in the (10, 10, 200, 200) area, you can configure the code as shown below.

```cpp
// Declare the class member variable as follows.
// CExamUIDlg Dialog
class CExamUIDlg : public CDialogEx
{
private:
    CMFCColorBar m_color_rect_list;

// ...
```

```cpp
// CExamUIDlg Message Handler
BOOL CExamUIDlg::OnInitDialog()
{
    CDialogEx::OnInitDialog();
 
    SetIcon(m_hIcon, TRUE);
    SetIcon(m_hIcon, FALSE);

    // Create a control 190 wide and 190 high at 10 and 10 positions.
    // The ID of this control is 2301 and displays 5 colors per line.
    m_color_rect_list.CreateControl(this, CRect(10, 10, 200, 200), 2301, 5);
    // Choose black from the colors listed.
    m_color_rect_list.SetColor(RGB(0, 0, 0));

    // ... The code below is omitted...
```

If you use the code above, the output is as follows. The borders of the controls are not displayed separately, so you can draw them further or use the Picture control to display them.

![Crepe](/assets/images/20230913_135943_224.png)

And if you want to adjust the size of the colored square area, you can use the SetHorzMargin, SetVertMargin functions as shown below.

![Crepe](/assets/images/20230913_135119_546.png)

```cpp
// Adjust the margins of the colored squares.
m_color_rect_list.SetHorzMargin(15);
m_color_rect_list.SetVertMargin(15);
// Add More Color Selection Button
m_color_rect_list.EnableOtherButton(L"Select different color");

// Create a control 190 wide and 190 high at 10 and 10 positions.
// The ID of this control is 2301 and displays 5 colors per line.
m_color_rect_list.CreateControl(this, CRect(10, 10, 200, 200), 2301, 5);
// Choose black from the colors listed.
m_color_rect_list.SetColor(RGB(0, 0, 0));
```

![Crepe](/assets/images/20230913_134629_199.png)

And when you change the color selection in this control, a WM_COMMAND message occurs, so if you want to do something when you change the color, you can add the ON_COMMAND macro to the Message Map as shown below. In this example, since the ID of the control was 2301, we put 2301 in the first factor of ON_COMMAND and named the function OnChangeColor to be processed when this message occurs.

```cpp
BEGIN_MESSAGE_MAP(CExamUIDlg, CDialogEx)
    ON_WM_PAINT()
    ON_WM_QUERYDRAGICON()
    ON_WM_DESTROY()
    ON_COMMAND(2301, OnChangeColor)
END_MESSAGE_MAP()
```

The OnChangeColor function adds the function prototype to the class header file as shown below.

```cpp
public:
    afx_msg void OnChangeColor();
```

You can add the function implementation to the class source file as shown below. It is recommended that you add these simple tasks yourself because the class wizard sometimes has problems adding user messages.

```cpp
void CExamUIDlg::OnChangeColor()
{
  // Gets the selected color value.
  COLORREF color = m_color_rect_list.GetColor();
  
  // Adding code that uses color

}
```
