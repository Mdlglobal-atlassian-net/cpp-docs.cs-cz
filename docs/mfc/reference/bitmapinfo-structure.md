---
title: "Bitmapinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BITMAPINFO
dev_langs: C++
helpviewer_keywords: BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 176f2434bd89c4adb826e214a7bf94e917e4d239
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO – struktura
`BITMAPINFO` Struktura definuje dimenzí a barevné informace pro Windows device independent bitmap (DIB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>Parametry  
 `bmiHeader`  
 Určuje [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) struktura, která obsahuje informace o dimenzí a barvu formát device independent bitmap.  
  
 `bmiColors`  
 Určuje pole [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) nebo `DWORD` datové typy, které definují barvy v souboru bitové mapy.  
  
## <a name="remarks"></a>Poznámky  
 Device independent bitmap se skládá ze dvou různých částí: `BITMAPINFO` struktura, která popisuje dimenzí a barvy bitovou mapu a pole bajtů, které určují pixelů v souboru bitové mapy. Bity v poli jsou zabaleny dohromady, ale každý řádek kontroly musí být doplněno nulami končí na `LONG` hranic. Pokud výška kladné, bitmapy pochází z levého dolního rohu. Pokud výška je hodnota záporná, je počátek levého horního rohu.  
  
 A *sbalené rastrový obrázek* je rastrový obrázek, kde následuje pole bajtů `BITMAPINFO` struktura. Zabalená bitmap odkazuje jeden ukazatel.  
  
 Další informace o `BITMAPINFO` struktury a příslušné hodnoty pro členy `BITMAPINFOHEADER` a `RGBQUAD` struktury, najdete v následujících tématech v dokumentaci k Windows SDK.  
  
- [Bitmapinfo – struktura](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
- [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) struktura  
  
- [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) struktura  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)

