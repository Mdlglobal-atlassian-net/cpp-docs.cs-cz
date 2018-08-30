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
ms.openlocfilehash: 0bc5adbb62e70a012d9dff4f9a390a46476aaa36
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200253"
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
 Určuje [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) strukturu, která obsahuje informace o dimenzích a formát barvy rastrového obrázku nezávislých na zařízení.  
  
 *bmiColors*  
 Určuje pole [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) nebo DWORD datové typy, které definují barvy rastrového obrázku nastaven.  
  
## <a name="remarks"></a>Poznámky  
 Bitmap nezávislých na zařízení se skládá ze dvou samostatných částí: `BITMAPINFO` struktura, která popisuje dimenze a barvy rastrového obrázku a pole bajtů, které určují pixely rastrového obrázku nastaven. Bity v pole jsou zkomprimována společně, ale každý řádek kontroly musí být doplněny nulami skončí **dlouhé** hranic. Při pozitivní výšku rastrového obrázku pochází z levého dolního rohu. Pokud je záporné, původ levém horním rohu.  
  
 A *komprimovat komprimovaný objekt bitmap* je rastrový obrázek, ve kterém následuje bajtového pole `BITMAPINFO` struktury. Komprimovat komprimovaný objekt Bitmap odkazuje jeden ukazatel.  
  
 Další informace o `BITMAPINFO` struktury a vhodné hodnoty pro členy programu `BITMAPINFOHEADER` a `RGBQUAD` struktury, naleznete v následujících tématech v dokumentaci Windows SDK.  
  
- [Bitmapinfo – struktura](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo)  
  
- [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) struktura  
  
- [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) struktura  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)

