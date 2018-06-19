---
title: 'Postupy: kreslení obrazců pomocí rozhraní .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 877e78b1ce4f81af76aa20961ea05d18e64f58f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130032"
---
# <a name="how-to-draw-shapes-with-the-net-framework"></a>Postupy: Kreslení tvarů s použitím rozhraní .NET Framework
Následující příklad kódu používá <xref:System.Drawing.Graphics> třída změnit <xref:System.Windows.Forms.Form.OnPaint%2A> obslužné rutiny události pro načtení ukazatel na <xref:System.Drawing.Graphics> objekt pro hlavní formulář. Tento ukazatel je pak používá k nastavení barvy pozadí formuláře a nakreslení čáry a oblouku pomocí <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> a <xref:System.Drawing.Graphics.DrawArc%2A> metody.  
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Hodnot System::Drawing](https://msdn.microsoft.com/en-us/library/system.drawing.aspx)