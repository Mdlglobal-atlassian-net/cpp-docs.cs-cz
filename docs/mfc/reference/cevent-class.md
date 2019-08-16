---
title: CEvent – třída
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: fbf2d834163199107aae44bd5723ceff79e36f91
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506679"
---
# <a name="cevent-class"></a>CEvent – třída

Představuje událost, což je synchronizační objekt, který umožňuje jednomu vláknu oznamovat jiné, že došlo k události.

## <a name="syntax"></a>Syntaxe

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|`CEvent` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CEvent::P ulseEvent](#pulseevent)|Nastaví událost na k dispozici (signalizaci), uvolní vlákna čekající na vyřízení a nastaví událost na nedostupnou (nesignalizované).|
|[CEvent::ResetEvent](#resetevent)|Nastaví událost na nedostupné (nesignalizované).|
|[CEvent:: SetEvent](#setevent)|Nastaví událost na k dispozici (signalizaci) a uvolní všechna čekací vlákna.|
|[CEvent:: Unlock](#unlock)|Uvolní objekt události.|

## <a name="remarks"></a>Poznámky

Události jsou užitečné v případě, kdy vlákno musí zjistit, kdy se má provést jeho úloha. Například vlákno, které kopíruje data do archivu dat, musí být oznámeno, když jsou k dispozici nová data. Pomocí `CEvent` objektu pro upozorňování vlákna kopírování, když jsou k dispozici nová data, vlákno může svou úlohu co nejdříve provést.

`CEvent`objekty mají dva typy: ruční a automatická.

Automatický `CEvent` objekt se automaticky vrátí do stavu bez signálu (není k dispozici) po uvolnění alespoň jednoho vlákna. Ve výchozím nastavení je `CEvent` objekt automaticky, pokud `TRUE` nepředáte parametru *bManualReset* během vytváření.

Ruční `CEvent` objekt zůstane ve stavu nastaveném funkcí [SetEvent](#setevent) nebo [ResetEvent](#resetevent) , dokud není volána jiná funkce. Chcete-li vytvořit `CEvent` ruční objekt, `TRUE` předejte `bManualReset` parametr během konstrukce.

Chcete-li `CEvent` použít objekt, `CEvent` Sestavte objekt, když je vyžadován. Zadejte název události, na které chcete čekat, a také určete, že aplikace by ji měla zpočátku vlastnit. Pak můžete k události přistupovat, když se konstruktor vrátí. Zavolejte [SetEvent](#setevent) k signalizaci (zpřístupnit) objektu události a potom zavolejte na [odemknout](#unlock) , když jste dokončili přístup k řízenému prostředku.

Alternativním způsobem použití `CEvent` objektů je přidat proměnnou typu `CEvent` jako datový člen do třídy, kterou chcete ovládat. Během konstrukce kontrolovaného objektu zavolejte konstruktor `CEvent` datového členu a určete, zda je událost zpočátku signalizována, a také specifythe typ objektu události, který chcete, název události (Pokud se bude používat napříč procesy). hranice) a všechny požadované atributy zabezpečení.

Chcete-li získat přístup k prostředku `CEvent` , který ovládá objekt tímto způsobem, nejprve vytvořte proměnnou typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo zadejte [CMultiLock](../../mfc/reference/cmultilock-class.md) v metodě přístupu svého prostředku. Pak zavolejte `Lock` metodu objektu Lock (například [CMultiLock:: Lock](../../mfc/reference/cmultilock-class.md#lock)). V tomto okamžiku vaše vlákno získá přístup k prostředku, počká na uvolnění prostředku a získá přístup, nebo počkejte na uvolnění prostředku, vypršení časového limitu a nepodaří se mu získat přístup k prostředku. V každém případě byl k vašemu prostředku přístup bezpečným způsobem. Chcete-li uvolnit prostředek, `SetEvent` zavolejte k signalizaci objektu události a pak `Unlock` použijte metodu objektu Lock (například [CMultiLock:: Unlock](../../mfc/reference/cmultilock-class.md#unlock)), nebo nechte objekt zámku mimo rozsah.

Další informace o použití `CEvent` objektů naleznete v tématu [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt. h

##  <a name="cevent"></a>CEvent::CEvent

Vytvoří pojmenovaný nebo nepojmenovaný `CEvent` objekt.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
Je-li nastaveno na hodnotu true `CMultilock` , `CSingleLock` je vlákno objektu nebo povoleno. V opačném případě musí počkat všechna vlákna, která chtějí získat přístup k prostředku.

*bManualReset*<br/>
Pokud je nastaveno na TRUE, určuje, že objekt události je ruční událost, jinak objekt události je automatická událost.

*lpszName*<br/>
`CEvent` Název objektu. Je nutné zadat, pokud se objekt bude používat napříč hranicemi procesu. Pokud název odpovídá existující události, konstruktor vytvoří nový `CEvent` objekt, který bude odkazovat na událost daného názvu. Pokud se název shoduje se stávajícím synchronizačním objektem, který není událost, konstrukce se nezdaří. Pokud má hodnotu NULL, bude mít název hodnotu null.

*lpsaAttribute*<br/>
Atributy zabezpečení pro objekt události Úplný popis této struktury naleznete v tématu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) v Windows SDK.

### <a name="remarks"></a>Poznámky

Chcete-li získat přístup `CEvent` k objektu nebo ho uvolnit, vytvořte objekt [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) a zavolejte jeho funkci [Lock](../../mfc/reference/csinglelock-class.md#lock) a [Odemkněte](../../mfc/reference/csinglelock-class.md#unlock) členské funkce.

Chcete-li změnit stav `CEvent` objektu na signál (vlákna nemusí čekat), zavolejte [SetEvent](#setevent) nebo [PulseEvent](#pulseevent). Chcete-li nastavit stav `CEvent` objektu na nesignálný (vlákna musí čekat), zavolejte [ResetEvent](#resetevent).

> [!IMPORTANT]
>  Po vytvoření `CEvent` objektu použijte příkaz [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby se zajistilo, že mutex ještě neexistoval. Pokud Mutex neočekávaně existoval, může to znamenat, že neoprávněný proces je squatting a může vycházet z škodlivého použití mutexu. V tomto případě je doporučený postup pro zaznamenání zabezpečení zavřít a pokračovat, jako kdyby došlo k chybě při vytváření objektu.

##  <a name="pulseevent"></a>CEvent::P ulseEvent

Nastaví stav události na signál (k dispozici), uvolní všechna čekací vlákna a obnoví je na nesignální (není k dispozici) automaticky.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla funkce úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud je událost ruční, jsou uvolněna všechna čekající vlákna, událost je nastavena na nesignalizaci a `PulseEvent` vrátí. Pokud je událost automaticky, jedno vlákno je uvolněno, událost je nastavena na nesignalizaci a `PulseEvent` vrátí.

Pokud nečekají žádná vlákna, nebo není možné okamžitě uvolnit žádná vlákna, `PulseEvent` nastaví stav události na nesignalizaci a vrátí.

`PulseEvent`používá základní funkci Win32 `PulseEvent` , která může být koncovým programem odebrána ze stavu čekání pomocí asynchronní procedury v režimu jádra. `PulseEvent` Proto je nespolehlivá a neměla by být používána novými aplikacemi. Další informace najdete v tématu [funkce PulseEvent](/windows/win32/api/winbase/nf-winbase-pulseevent).

##  <a name="resetevent"></a>CEvent::ResetEvent

Nastaví stav události na nesignalizaci, dokud není explicitně nastaveno na signál členskou funkcí [SetEvent](#setevent) .

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla funkce úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

To způsobí, že všechna vlákna, která chtějí získat přístup k této události, budou čekat.

Tato členská funkce se nepoužívá v automatických událostech.

##  <a name="setevent"></a>CEvent:: SetEvent

Nastaví stav události k signalizaci a uvolnění všech čekajících vláken.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla funkce úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je událost ruční, zůstane událost signalizována až po volání [ResetEvent](#resetevent) . V tomto případě lze vydat více než jedno vlákno. Pokud je událost automatická, událost zůstane signalizována, dokud se neuvolní jedno vlákno. Systém pak nastaví stav události na nesignalizace. Pokud žádná vlákna nečekají, stav zůstane signalizována, dokud se neuvolní jedno vlákno.

##  <a name="unlock"></a>CEvent:: Unlock

Uvolní objekt události.

```
BOOL Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vlákno vlastně objekt události a událost je automatická událost; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána vlákny, které aktuálně vlastní událost pro uvolnění po jejich dokončení, pokud je jejich objekt zámku znovu použit. Pokud objekt zámku není znovu použit, bude tato funkce volána destruktorem objektu zámku.

## <a name="see-also"></a>Viz také:

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
