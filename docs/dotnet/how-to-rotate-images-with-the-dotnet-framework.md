---
title: "Postupy: otáčení obrázků s použitím rozhraní .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], rotating images
- graphics [C++], rotating images
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5b337186f67758d56dbc0bae06b6886f43f7435
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-rotate-images-with-the-net-framework"></a>Postupy: Otáčení obrázků s použitím rozhraní .NET Framework
Následující příklad kódu ukazuje použití <xref:System.Drawing.Image?displayProperty=fullName> třída načíst obrázek z disku, rotaci o 90 stupňů a uložte ho jako nový soubor .jpg.  
  
> [!NOTE]
>  GDI + je součástí systému Windows XP a je k dispozici jako redistributable pro systém Windows NT 4.0 aktualizace Service Pack 6, Windows 2000, Windows 98 a Windows Millennium Edition. Si můžete stáhnout nejnovější distribuovatelné [http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232). 
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)