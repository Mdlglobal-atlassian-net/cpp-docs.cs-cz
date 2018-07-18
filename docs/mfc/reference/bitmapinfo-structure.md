---
title: Bitmapinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAPINFO
dev_langs:
- C++
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9b1bd896157d7f11792a5a6514e30ecd3d46a19
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336254"
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO – struktura
`BITMAPINFO` Struktury definuje rozměry a informace o barvě pro Windows device independent bitmap (DIB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>Parametry  
 *bmiHeader*  
 Určuje [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) strukturu, která obsahuje informace o dimenzích a formát barvy rastrového obrázku nezávislých na zařízení.  
  
 *bmiColors*  
 Určuje pole [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) nebo DWORD datové typy, které definují barvy rastrového obrázku nastaven.  
  
## <a name="remarks"></a>Poznámky  
 Bitmap nezávislých na zařízení se skládá ze dvou samostatných částí: `BITMAPINFO` struktura, která popisuje dimenze a barvy rastrového obrázku a pole bajtů, které určují pixely rastrového obrázku nastaven. Bity v pole jsou zkomprimována společně, ale každý řádek kontroly musí být doplněny nulami skončí **dlouhé** hranic. Při pozitivní výšku rastrového obrázku pochází z levého dolního rohu. Pokud je záporné, původ levém horním rohu.  
  
 A *komprimovat komprimovaný objekt bitmap* je rastrový obrázek, ve kterém následuje bajtového pole `BITMAPINFO` struktury. Komprimovat komprimovaný objekt Bitmap odkazuje jeden ukazatel.  
  
 Další informace o `BITMAPINFO` struktury a vhodné hodnoty pro členy programu `BITMAPINFOHEADER` a `RGBQUAD` struktury, naleznete v následujících tématech v dokumentaci Windows SDK.  
  
- [Bitmapinfo – struktura](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
- [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) struktura  
  
- [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) struktura  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)

