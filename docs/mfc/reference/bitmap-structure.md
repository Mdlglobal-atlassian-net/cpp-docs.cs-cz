---
title: Rastrový OBRÁZEK strukturu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56e93bf1485cefed9a44e0e6260358650ab8b296
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032585"
---
# <a name="bitmap-structure"></a>BITMAP – struktura
**Rastrový OBRÁZEK** struktury definuje výšku, šířku, formát barev a bitové hodnoty logického rastrového obrázku **.**  
  
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
 Určuje počet bajtů v každém rastrovém řádku. Tato hodnota musí být sudým číslem, protože rozhraní GDI (Graphics Device Interface) předpokládá, že bitové hodnoty rastrového obrázku tvoří pole celočíselných (2bajtových) hodnot. Jinými slovy *bmWidthBytes* \* 8 musí být dalším násobkem 16 větší než nebo rovna hodnotě získané *bmWidth* členem *bmBitsPixel*  člena.  
  
 *bmPlanes*  
 Určuje počet barevných rovin rastrového obrázku.  
  
 *bmBitsPixel*  
 Určuje, kolik sousedních bitů barev každé roviny je zapotřebí k definování pixelu.  
  
 *bmBits*  
 Ukazuje na umístění bitových hodnot rastrového obrázku. *BmBits* člen musí být dlouhým ukazatelem na pole 1bajtových hodnot.  
  
## <a name="remarks"></a>Poznámky  
 Aktuálně používané formáty rastrových obrázků jsou monochromatický a barevný. Monochromatický rastrový obrázek používá 1bitový formát s jednou rovinou. Každý průchod je násobkem 16 bitů.  
  
 Jsou průchody uspořádány takto pro monochromatický rastrový obrázek výšky *n*:  
  
```
Scan 0
Scan 1
.
.
.
Scan n-2
Scan n-1
```
  
 Pixely monochromatického zařízení jsou buď černé, nebo bílé. Je-li odpovídající bit rastrového obrázku nastaven na hodnotu 1, je pixel zapnut (bílý). Je-li odpovídající bit rastrového obrázku nastaven na hodnotu 0, je pixel vypnut (černý).  
  
 Všechna zařízení podporují rastrové obrázky, mít nastavený RC_BITBLT bit RASTERCAPS index [CDC::GetDeviceCaps](../../mfc/reference/cdc-class.md#getdevicecaps) členskou funkci.  
  
 Každé zařízení má svůj vlastní jedinečný formát barev. Chcete-li přenášet rastrové obrázky z jednoho zařízení do druhého, použijte [GetDIBits](/windows/desktop/api/wingdi/nf-wingdi-getdibits) a [SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits) funkce Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
