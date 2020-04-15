---
title: Funkce zpětného volání používané v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 8d84f939795e768c6b1356dcd8dc291421aedfdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371129"
---
# <a name="callback-functions-used-by-mfc"></a>Funkce zpětného volání používané v prostředí MFC

V knihovně tříd Microsoft Foundation se zobrazí tři funkce zpětného volání. Tyto funkce zpětného volání jsou předány [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)a [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Všimněte si, že všechny funkce zpětného volání musí soutisk mfc výjimky před návratem do systému Windows, protože výjimky nelze vyvolat přes hranice zpětného volání. Další informace o výjimkách naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

|Name (Název)||
|----------|-----------------|
|[Funkce zpětného volání pro metodu CDC::EnumObjects](#enum_objects)||
|[Funkce zpětného volání pro metodu CDC::GrayString](#graystring)||
|[Funkce zpětného volání pro metodu CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>Funkce zpětného volání pro CDC::EnumObjects

Název *ObjectFunc* je zástupný symbol pro název funkce zadané aplikací.

### <a name="syntax"></a>Syntaxe

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parametry

*lpszLogObject*<br/>
Odkazuje na datovou strukturu [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) nebo [LOGBRUSH,](/windows/win32/api/wingdi/ns-wingdi-logbrush) která obsahuje informace o logických atributech objektu.

*lpData*<br/>
Odkazuje na data dodaná `EnumObjects` aplikací předaná funkci.

### <a name="return-value"></a>Návratová hodnota

Funkce zpětného volání vrátí **int**. Hodnota tohoto vrácení je definována uživatelem. Pokud funkce zpětného volání `EnumObjects` vrátí 0, zastaví výčet brzy.

### <a name="remarks"></a>Poznámky

Skutečný název musí být exportován.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>Funkce zpětného volání pro CDC::GrayString

*OutputFunc* je zástupný symbol pro název funkce zpětného volání dodané aplikací.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
Identifikuje kontext paměťového zařízení s bitmapou alespoň šířky `nWidth` `nHeight` a `GrayString`výšky určené aplikací a do .

*lpData*<br/>
Odkazuje na řetězec znaků, který chcete kreslit.

*nCount*<br/>
Určuje počet znaků pro výstup.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota funkce zpětného volání musí být TRUE, aby byla indikována úspěšnost; jinak je false.

### <a name="remarks"></a>Poznámky

Funkce zpětného volání (*OutputFunc*) musí nakreslit obrázek vzhledem ke souřadnicím (0,0) spíše než (*x*, *y*).

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>Funkce zpětného volání pro CDC::SetAbortProc

Název *AbortFunc* je zástupný symbol pro název funkce zadané aplikací.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parametry

*hPr*<br/>
Identifikuje kontext zařízení.

*Kód*<br/>
Určuje, zda došlo k chybě. Je 0, pokud došlo k žádné chybě. Je SP_OUTOFDISK, pokud správce tisku je aktuálně nedostatek místa na disku a více místa na disku bude k dispozici, pokud aplikace čeká. Pokud je *kód* SP_OUTOFDISK, aplikace nemusí přerušit tiskovou úlohu. Pokud tomu tak není, musí výnos správce `PeekMessage` tisku `GetMessage` voláním funkce nebo Windows.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota funkce abort-handler je nenulová, pokud má tisková úloha pokračovat, a 0, pokud je zrušena.

### <a name="remarks"></a>Poznámky

Skutečný název musí být exportován, jak je popsáno v části Poznámky [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::Štěňata](../../mfc/reference/cdc-class.md#graystring)
