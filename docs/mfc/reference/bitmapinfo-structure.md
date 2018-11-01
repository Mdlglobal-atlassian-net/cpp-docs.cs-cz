---
title: BITMAPINFO – struktura
ms.date: 11/04/2016
f1_keywords:
- BITMAPINFO
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
ms.openlocfilehash: 8e0586d197bc2f18a06fd675bf365750c6d129ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542269"
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

*bmiHeader*<br/>
Určuje [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) strukturu, která obsahuje informace o dimenzích a formát barvy rastrového obrázku nezávislých na zařízení.

*bmiColors*<br/>
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

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)<br/>
[BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)<br/>
[RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)

