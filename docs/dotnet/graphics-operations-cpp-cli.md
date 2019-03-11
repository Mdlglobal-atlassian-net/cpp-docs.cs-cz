---
title: Grafické operace (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- GDI+ [C++]
- .NET Framework [C++], graphics
- images [C++], .NET Framework and
- GDI+ [C++], about graphics operations
- graphics [C++], .NET Framework and
- GDI+ [C++], displaying images
- graphics [C++], displaying images
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
- GDI+ [C++], rotating images
- graphics [C++], rotating images
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: bba27228-b9b3-4c9c-b31c-a04b76702a95
ms.openlocfilehash: c7c6d62eb4059069e6e266544ce6323c63dd15c0
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746276"
---
# <a name="graphics-operations-ccli"></a>Grafické operace (C++/CLI)

Ukazuje zpracování obrázků pomocí sady Windows SDK.

Následující témata ukazují použití <xref:System.Drawing.Image?displayProperty=fullName> pro provádění zpracování obrázků.

## <a name="display"></a> Zobrazení obrázků s použitím rozhraní .NET Framework

Následující příklad upravuje obslužná rutina události OnPaint níž načítají ukazatel na <xref:System.Drawing.Graphics> objektu pro hlavní formulář. <xref:System.Windows.Forms.Form.OnPaint%2A> Funkce je určená pro aplikace Windows Forms, pravděpodobně vytvořené pomocí Průvodce aplikace Visual Studio.

Na obrázku je reprezentována <xref:System.Drawing.Image> třídy. Načtení dat obrázků pomocí soubor .jpg <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> metody. Předtím, než na obrázku je vykreslen do formuláře, formuláře je velikost obrázku. Kreslení obrázku se pomocí provádí <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> metody.

<xref:System.Drawing.Graphics> a <xref:System.Drawing.Image> třídy jsou v <xref:System.Drawing?displayProperty=fullName> oboru názvů.

### <a name="example"></a>Příklad

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override
{
    Graphics^ g = pe->Graphics;
    Image^ image = Image::FromFile("SampleImage.jpg");
    Form::ClientSize = image->Size;
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );
}
```

## <a name="draw"></a> Kreslení tvarů s použitím rozhraní .NET Framework

Následující příklad kódu používá <xref:System.Drawing.Graphics> třídy k úpravě <xref:System.Windows.Forms.Form.OnPaint%2A> obslužnou rutinu události pro načtení ukazatel <xref:System.Drawing.Graphics> objektu pro hlavní formulář. Tento ukazatel je pak používá k nastavení barvy pozadí formuláře a nakreslení čáry a oblouku pomocí <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> a <xref:System.Drawing.Graphics.DrawArc%2A> metody.

### <a name="example"></a>Příklad

```cpp
#using <system.drawing.dll>
using namespace System;
using namespace System::Drawing;
// ...
protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override
{
   Graphics^ g = pe->Graphics;
   g->Clear(Color::AntiqueWhite);

   Rectangle rect = Form::ClientRectangle;
   Rectangle smallRect;
   smallRect.X = rect.X + rect.Width / 4;
   smallRect.Y = rect.Y + rect.Height / 4;
   smallRect.Width = rect.Width / 2;
   smallRect.Height = rect.Height / 2;

   Pen^ redPen = gcnew Pen(Color::Red);
   redPen->Width = 4;
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);

   Pen^ bluePen = gcnew Pen(Color::Blue);
   bluePen->Width = 10;
   g->DrawArc( bluePen, smallRect, 90, 270 );
}
```

## <a name="rotate"></a> Otáčení obrázků s použitím rozhraní .NET Framework

Následující příklad kódu ukazuje použití <xref:System.Drawing.Image?displayProperty=fullName> třídy k načtení obrázku z disku, otočit o 90 stupňů a uložte ho jako nový soubor .jpg.

### <a name="example"></a>Příklad

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );
   image->Save("SampleImage_rotated.jpg");
   return 0;
}
```

## <a name="convert"></a> Převod formátu souborů obrázků s použitím rozhraní .NET Framework

Následující příklad kódu ukazuje <xref:System.Drawing.Image?displayProperty=fullName> třídy a <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> výčet používané k převádění a uložte soubory bitových kopií. Následující kód načte obrázek ze souboru JPG a uloží ho do formátů souborů .gif a BMP.

### <a name="example"></a>Příklad

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;
using namespace System::Drawing::Imaging;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->Save("SampleImage.png", ImageFormat::Png);
   image->Save("SampleImage.bmp", ImageFormat::Bmp);

   return 0;
}
```

## <a name="related-sections"></a>Související oddíly

[Začínáme s programováním grafiky](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[Informace o spravovaném kódu GDI+](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>Viz také:

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
