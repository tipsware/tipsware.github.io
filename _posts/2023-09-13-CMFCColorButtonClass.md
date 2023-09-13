---
layout: post
title: CMFCColorBar Class
subtitle: CMFCColorBar Class
author: Baeco
categories: MFC
banner:
  image: https://postfiles.pstatic.net/MjAyMzA5MTNfNjUg/MDAxNjk0NTgxNTkyNzM0.s5FPklQrdyOovFfLzGwAEyZV-9E5m7eDYWuDnFaeUZUg.h5OZdRLLPsXV5QepTRwDB5yX6uMOwKdO60-ah6kZrVcg.PNG.tipsware/KakaoTalk_20230702_175319468.png
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: mfc cmfccolorbutton
top: 1
sidebar: []
---

## CMFColorButton

CMFColorButton, which is provided in the form of a combo box when selecting a color, is effective when there is not enough UI space, but it has the disadvantage of increasing the number of clicks for color selection. 

And CMFColorDialog can be selected while looking at many colors at once, but it's inevitably uncomfortable if you have to choose repeatedly because you have to work with a dialog box every time.


Therefore, the class that allows CMFColorButton to be used in the form of a list box is the CMFColorBar class. This class allows you to list and select colors as shown below. 

This class also provides a 'select another color' function immediately, so you don't need to add a separate CMFColorDialog usage code when you need additional colors.


![Crepe](https://mblogvideo-phinf.pstatic.net/MjAyMzA5MTNfNjMg/MDAxNjk0NTc5NTYyNjU3.bRADCjouXO7qM4AyVRFaXp2N0Z_IAWt_TRNtc26jVg0g.IpKedAmi1Oy24CUaUJPPeqvenz3Iiw_CMsDi_z2nxUQg.GIF.tipsware/color_bar1.GIF)


Because this control cannot be selected in the Resource Editor, you must create it by giving it your own coordinates and IDs. 

For example, if you want to create this control with the control ID 2301 in the (10, 10, 200, 200) area, you can configure the code as shown below.

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

// ...
```

If you use the code above, the output is as follows. The borders of the controls are not displayed separately, 

so you can draw them further or use the Picture control to display them.

![Crepe](https://postfiles.pstatic.net/MjAyMzA5MTNfMTcg/MDAxNjk0NTgwNjg1OTQx.0SfWxJAhCzoHgzKYnphUPAI-kpH89U3KBGWKJSgI2w4g.Zs2czTZU8uLXLn8oSiQRnhNNk4T95Kx2c-ITEhbIxmAg.PNG.tipsware/20230913_135119_546.png)



## section 2

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]: https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

$ a \* b = c ^ b $

$ 2^{\frac{n-1}{3}} $

$ \int_a^b f(x)\,dx. $

```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "Hello World!";
  return 0;
}
// prints 'Hi, Tom' to STDOUT.
```

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("John", 36)

print(p1.name)
print(p1.age)
```
