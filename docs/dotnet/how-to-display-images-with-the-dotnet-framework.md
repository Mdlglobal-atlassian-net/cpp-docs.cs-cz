---
title: "Postupy: zobrazení obrázků s použitím rozhraní .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7c12d6a67f6fbe73802d3b876621a2ea606af553
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-display-images-with-the-net-framework"></a>Postupy: Zobrazení obrázků s použitím rozhraní .NET Framework
Následující příklad kódu upraví OnPaint obslužné rutiny události pro načtení ukazatel <xref:System.Drawing.Graphics> objekt pro hlavní formulář. <xref:System.Windows.Forms.Form.OnPaint%2A> Funkce je určena pro aplikaci Windows Forms, pravděpodobně vytvořené pomocí Průvodce aplikace Visual Studio.  
  
 Obrázek je reprezentována <xref:System.Drawing.Image> třídy. Načtení dat bitovou kopii pomocí souboru JPG <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> metoda. Před bitovou kopii vykreslením do formuláře, formuláře se změnila velikost pro umístění image. Kreslení obrázku se provádí pomocí <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> metoda.  
  
 <xref:System.Drawing.Graphics> a <xref:System.Drawing.Image> třídy jsou v i <xref:System.Drawing?displayProperty=fullName> oboru názvů.  
  
> [!NOTE]
>  Rozhraní GDI + je součástí systému Windows XP a je k dispozici jako redistributable pro systém Windows NT 4.0 aktualizace Service Pack 6, Windows 2000, Windows 98 a Windows Me. Si můžete stáhnout nejnovější distribuovatelné [http://go.microsoft.com/fwlink/p/?linkid=11232](http://go.microsoft.com/fwlink/p/?linkid=11232).   
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing?displayProperty=fullName>   
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)