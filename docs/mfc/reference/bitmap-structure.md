---
title: "Struktura rastrový OBRÁZEK | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ed782c3e67a55797bfb2d302265924393946962
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bitmap-structure"></a>BITMAP – struktura
**Rastrový OBRÁZEK** struktura definuje výška, šířka, formát barvy a bitových hodnot logické rastrový obrázek**.**  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagBITMAP {  /* bm */  
    int bmType;  
    int bmWidth;  
    int bmHeight;  
    int bmWidthBytes;  
    BYTE bmPlanes;  
    BYTE bmBitsPixel;  
    LPVOID bmBits;  
} BITMAP;  
```  
  
#### <a name="parameters"></a>Parametry  
 *bmType*  
 Určuje typ rastrového obrázku. V případě logických rastrových obrázků musí být tento člen nastaven na hodnotu 0.  
  
 *bmWidth*  
 Určuje šířku rastrového obrázku v pixelech. Šířka musí být větší než 0.  
  
 *bmHeight*  
 Určuje výšku rastrového obrázku v rastrových řádcích. Výška musí být větší než 0.  
  
 *bmWidthBytes*  
 Určuje počet bajtů v každém rastrovém řádku. Tato hodnota musí být sudým číslem, protože rozhraní GDI (Graphics Device Interface) předpokládá, že bitové hodnoty rastrového obrázku tvoří pole celočíselných (2bajtových) hodnot. Jinými slovy **bmWidthBytes** \* 8 musí být další násobkem 16 větší než nebo rovna hodnotě získali, když **bmWidth** člen se násobí hodnotou **bmBitsPixel**  člen.  
  
 *bmPlanes*  
 Určuje počet barevných rovin rastrového obrázku.  
  
 *bmBitsPixel*  
 Určuje, kolik sousedních bitů barev každé roviny je zapotřebí k definování pixelu.  
  
 *bmBits*  
 Ukazuje na umístění bitových hodnot rastrového obrázku. **BmBits** člena musí být dlouhé ukazatel na pole 1bajtový hodnot.  
  
## <a name="remarks"></a>Poznámky  
 Aktuálně používané formáty rastrových obrázků jsou monochromatický a barevný. Monochromatický rastrový obrázek používá 1bitový formát s jednou rovinou. Každý průchod je násobkem 16 bitů.  
  
 Kontroly jsou uspořádány takto černobílý rastrového obrázku výšky  *n* :  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 Pixely monochromatického zařízení jsou buď černé, nebo bílé. Je-li odpovídající bit rastrového obrázku nastaven na hodnotu 1, je pixel zapnut (bílý). Je-li odpovídající bit rastrového obrázku nastaven na hodnotu 0, je pixel vypnut (černý).  
  
 Všechna zařízení podporují rastrové obrázky, které mají **RC_BITBLT** v nastaven bit **RASTERCAPS** index [CDC::GetDeviceCaps](../../mfc/reference/cdc-class.md#getdevicecaps) – členská funkce.  
  
 Každé zařízení má svůj vlastní jedinečný formát barev. Chcete-li přenášet rastrový obrázek z jednoho zařízení do druhého, použijte [GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879) a [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) funkce systému Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
