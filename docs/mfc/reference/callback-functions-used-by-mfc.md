---
title: Funkce zpětného volání používané v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 9e51774b2158a81fce05dc0bd27e296e4ad94faa
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855472"
---
# <a name="callback-functions-used-by-mfc"></a>Funkce zpětného volání používané v prostředí MFC

V knihovna Microsoft Foundation Class se zobrazí tři funkce zpětného volání. Tyto funkce zpětného volání jsou předány do [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC:: GrayString](../../mfc/reference/cdc-class.md#graystring)a [CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Všimněte si, že všechny funkce zpětného volání musí před návratem do systému Windows zachytit výjimky knihovny MFC, protože výjimky nelze vyvolat přes hranice zpětného volání. Další informace o výjimkách najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

|Název||
|----------|-----------------|
|[Funkce zpětného volání pro metodu CDC::EnumObjects](#enum_objects)||
|[Funkce zpětného volání pro metodu CDC::GrayString](#graystring)||
|[Funkce zpětného volání pro metodu CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="enum_objects"></a>Funkce zpětného volání pro funkci CDC:: EnumObjects

Název *ObjectFunc* je zástupný symbol pro název funkce dodané aplikací.

### <a name="syntax"></a>Syntaxe

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parametry

*lpszLogObject*<br/>
Odkazuje na strukturu dat [LOGPEN –](/windows/win32/api/Wingdi/ns-wingdi-logpen) nebo [LOGBRUSH –](/windows/win32/api/wingdi/ns-wingdi-logbrush) , která obsahuje informace o logických atributech objektu.

*lpData*<br/>
Odkazuje na data poskytnutá aplikací předaná funkci `EnumObjects`.

### <a name="return-value"></a>Návratová hodnota

Funkce zpětného volání vrací **int**. Hodnota tohoto návratu je definovaná uživatelem. Pokud funkce zpětného volání vrátí hodnotu 0, `EnumObjects` zastaví výčet na začátku.

### <a name="remarks"></a>Poznámky

Skutečný název musí být exportován.

## <a name="graystring"></a>Funkce zpětného volání pro funkci CDC:: GrayString

*OutputFunc* je zástupný symbol pro název funkce zpětného volání dodaného aplikací.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parametry

*hDC*<br/>
Identifikuje kontext paměťového zařízení s rastrovým obrázkem s minimální šířkou a výškou určenou `nWidth` a `nHeight` na `GrayString`.

*lpData*<br/>
Odkazuje na řetězec znaků, který chcete kreslit.

*nCount*<br/>
Určuje počet znaků pro výstup.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota funkce zpětného volání musí mít hodnotu TRUE, aby označovala úspěch; v opačném případě je hodnota FALSE.

### <a name="remarks"></a>Poznámky

Funkce zpětného volání (*OutputFunc*) musí nakreslit obrázek relativně k souřadnicím (0, 0) místo (*x*, *y*).

## <a name="setabortproc"></a>Funkce zpětného volání pro funkci CDC:: SetAbortProc

Název *AbortFunc* je zástupný symbol pro název funkce dodané aplikací.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parametry

*hPr*<br/>
Identifikuje kontext zařízení.

*znakovou*<br/>
Určuje, zda došlo k chybě. Je 0, pokud nedošlo k žádné chybě. Je SP_OUTOFDISK v případě, že správce tisku aktuálně nemá volné místo na disku a další místo na disku bude k dispozici, pokud aplikace počká. Pokud je *kód* SP_OUTOFDISK, aplikace nemusí přerušit tiskovou úlohu. Pokud tomu tak není, musí poskytnout správci tisku voláním `PeekMessage` nebo `GetMessage` funkce Windows.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota funkce Abort-Handler je nenulová, Pokud tisková úloha pokračuje a 0, pokud je zrušena.

### <a name="remarks"></a>Poznámky

Skutečný název musí být exportován, jak je popsáno v části poznámky v tématu [CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC:: GrayString](../../mfc/reference/cdc-class.md#graystring)
