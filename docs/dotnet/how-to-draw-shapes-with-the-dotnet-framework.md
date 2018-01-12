---
title: "Postupy: kreslení obrazců pomocí rozhraní .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 62579ca21ba4a4dcf89aea6ff717ce6c884073b3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-draw-shapes-with-the-net-framework"></a>Postupy: Kreslení tvarů s použitím rozhraní .NET Framework
Následující příklad kódu používá <xref:System.Drawing.Graphics> třída změnit <xref:System.Windows.Forms.Form.OnPaint%2A> obslužné rutiny události pro načtení ukazatel na <xref:System.Drawing.Graphics> objekt pro hlavní formulář. Tento ukazatel je pak používá k nastavení barvy pozadí formuláře a nakreslení čáry a oblouku pomocí <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> a <xref:System.Drawing.Graphics.DrawArc%2A> metody.  
  
> [!NOTE]
>  Rozhraní GDI + je součástí systému Windows XP a je k dispozici jako redistributable pro systém Windows NT 4.0 aktualizace Service Pack 6, Windows 2000, Windows 98 a Windows Me. Si můžete stáhnout nejnovější distribuovatelné [http://go.microsoft.com/fwlink/p/?linkid=11232](http://go.microsoft.com/fwlink/p/?linkid=11232). 
  
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