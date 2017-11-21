---
title: "Postupy: převod formátu souborů obrázků s použitím rozhraní .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: 5d5384b0-b9b7-4262-b9ad-c4cb95f75ee4
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eff94d00f92fe0a52162c986662209168974e072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-image-file-formats-with-the-net-framework"></a>Postupy: Převod formátu souborů obrázků s použitím rozhraní .NET Framework
Následující příklad kódu ukazuje <xref:System.Drawing.Image?displayProperty=fullName> třídy a <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> výčtu lze převést a uložit soubory obrázků. Následující kód načte obrázek ze souboru JPG a uloží ho do GIF a BMP formáty souborů.  
  
> [!NOTE]
>  Rozhraní GDI + je součástí systému Windows XP, Windows Server 2003 a Windows Vista a je k dispozici jako redistributable pro systém Windows 2000. Si můžete stáhnout nejnovější distribuovatelné [http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232).   
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing>   
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)