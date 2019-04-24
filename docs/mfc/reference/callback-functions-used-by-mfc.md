---
title: Funkce zpětného volání používané v prostředí MFC
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.functions
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: e3440530dfe30b6667012c76b2904dbb2786c199
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152140"
---
# <a name="callback-functions-used-by-mfc"></a>Funkce zpětného volání používané v prostředí MFC

Zobrazí tři funkce zpětného volání v knihovny Microsoft Foundation Class. Tyto funkce zpětného volání jsou předány [metodu CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [metodu CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), a [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Všimněte si, že všechny funkce zpětného volání musí zachycují výjimky MFC před vrácením Windows, protože výjimky nejde vyvolat přes hranice zpětného volání. Další informace o výjimkách, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

|Název||
|----------|-----------------|
|[Funkce zpětného volání pro metodu CDC::EnumObjects](#enum_objects)||
|[Funkce zpětného volání pro metodu CDC::GrayString](#graystring)||
|[Funkce zpětného volání pro metodu CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="enum_objects"></a> Funkce zpětného volání pro metodu CDC::EnumObjects

*ObjectFunc* název je zástupný symbol pro název funkce poskytované aplikací.

### <a name="syntax"></a>Syntaxe

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parametry

*lpszLogObject*<br/>
Odkazuje [logpen –](/windows/desktop/api/Wingdi/ns-wingdi-taglogpen) nebo [logbrush –](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) datová struktura, která obsahuje informace o logické atributy objektu.

*lpData*<br/>
Body k datům poskytované aplikací předaný `EnumObjects` funkce.

### <a name="return-value"></a>Návratová hodnota

Funkce zpětného volání vrátí **int**. Tato návratovou hodnotu definovaný uživatelem. Pokud funkce zpětného volání vrátí hodnotu 0, `EnumObjects` zastaví výčet již v rané fázi.

### <a name="remarks"></a>Poznámky

Skutečný název musí být exportován.

## <a name="graystring"></a>  Funkce zpětného volání pro metodu CDC::GrayString

*OutputFunc* je zástupný symbol pro název funkce poskytované aplikací zpětného volání.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parametry

*hDC*<br/>
Určuje kontext zařízení paměti s rastrový obrázek alespoň šířku a výšku určené `nWidth` a `nHeight` k `GrayString`.

*lpData*<br/>
Odkazuje na řetězec znaků, který chcete kreslit.

*nCount*<br/>
Určuje počet znaků výstupu.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota funkce zpětného volání musí být TRUE, čímž indikuje úspěšné provedení; v opačném případě je FALSE.

### <a name="remarks"></a>Poznámky

Funkce zpětného volání (*OutputFunc*) musí vykreslení obrázku vzhledem k souřadnice (0,0) místo (*x*, *y*).

## <a name="setabortproc"></a>  Funkce zpětného volání pro metodu CDC::SetAbortProc

Název *AbortFunc* je zástupný symbol pro název funkce poskytované aplikací.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parametry

*hPr*<br/>
Určuje kontext zařízení.

*code*<br/>
Určuje, zda došlo k chybě. To je 0, pokud nedojde k žádné chybě. Je SP_OUTOFDISK Pokud správce tisku právě volné místo na disku a bude k dispozici více místa na disku aplikace čeká. Pokud *kód* je SP_OUTOFDISK, aplikace nemusí přerušit tiskové úlohy. Pokud tomu tak není, musí poskytovat správce tisku pomocí volání `PeekMessage` nebo `GetMessage` funkce Windows.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota funkce obslužné rutiny přerušení je nenulová, pokud je chcete pokračovat, tiskové úlohy a 0 Pokud bude zrušen.

### <a name="remarks"></a>Poznámky

Skutečný název musí být exportován, jak je popsáno v části poznámky [metodu CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](structures-styles-callbacks-and-message-maps.md)<br/>
[Metodu CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[Metodu CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
