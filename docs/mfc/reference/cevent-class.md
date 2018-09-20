---
title: CEvent – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8dff47314c5e8932a6f5a2a2078fd70a86c9229b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386493"
---
# <a name="cevent-class"></a>CEvent – třída

Představuje událost, což je synchronizační objekt umožňující vždy jednomu vláknu upozornit jiné, že došlo k události.

## <a name="syntax"></a>Syntaxe

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Vytvoří `CEvent` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|Nastaví událost, která má k dispozici (signalizován), uvolní čekajících vláken a nastaví událost do nedostupný (nonsignaled).|
|[CEvent::ResetEvent](#resetevent)|Nastaví událost do nedostupný (nonsignaled).|
|[CEvent::SetEvent](#setevent)|Nastaví událost na k dispozici (signalizovaného) a uvolní všechny čekajících vláken.|
|[CEvent::Unlock](#unlock)|Verze objektu události.|

## <a name="remarks"></a>Poznámky

Události jsou užitečné, pokud vlákno musí vědět, kdy k provádění svých úloh. Například podproces, který kopíruje data do archivu dat musí být upozorněn, pokud je k dispozici nová data. Pomocí `CEvent` objekt upozornit nová data k dispozici, vlákno kopírování jeho úlohu lze provést nejdříve vlákna.

`CEvent` objekty mají dva typy: ruční a automatická.

Automatické `CEvent` objekt automaticky vrátí do nesignálového stavu (není k dispozici), po vydání alespoň jedno vlákno. Ve výchozím nastavení `CEvent` objekt je automatické, pokud nepředáte `TRUE` pro *bManualReset* parametru během vytváření.

Ruční `CEvent` objekt zůstane ve stavu nastavil [SetEvent](#setevent) nebo [ResetEvent](#resetevent) dokud jiná funkce je volána. Chcete-li vytvořit ruční `CEvent` objektu, předejte `TRUE` pro `bManualReset` parametru během vytváření.

Použití `CEvent` objektu, vytvořit `CEvent` objektu, pokud je to požadováno. Zadejte název události, kterou chcete čekat na a také určit, že vaše aplikace by měl původně jeho vlastnictví. Pak můžou události po návratu konstruktoru. Volání [SetEvent](#setevent) signál (zpřístupnit) objektu události a poté zavolejte [odemknout](#unlock) po dokončení přístup k řízenému prostředku.

Alternativní způsob pro použití `CEvent` objekty, je přidat proměnnou typu `CEvent` jako datový člen třídy, které chcete ovládací prvek. Během konstrukce objektu řízené volání konstruktoru `CEvent` datový člen a určit, zda událost je signalizována původně a také specifythe typ objektu event, který má název události (Pokud se použije v procesu hranice) a chcete, aby atributy zabezpečení.

Pro přístup k prostředku, řídí `CEvent` objektu tímto způsobem, musíte nejprve vytvořit proměnnou buď typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo typ [CMultiLock](../../mfc/reference/cmultilock-class.md) v metodě přístup k prostředku. Zavolejte `Lock` metodu zámek objektu (například [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). V tomto okamžiku vašeho vlákna budou buď získat přístup k prostředku, čekat na prostředek, který chcete uvolnit a získat přístup nebo počkejte prostředek, který má být uvolněna, vypršení časového limitu a nepovedlo se získat přístup k prostředku. V každém případě váš prostředek má byla přístupná takovým způsobem bezpečným pro vlákno. K uvolnění prostředku, volání `SetEvent` signalizuje, že objekt události, a pak použít `Unlock` metodu zámek objektu (například [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), nebo nechat zámek objektu spadá mimo rozsah.

Další informace o tom, jak používat `CEvent` objekty, najdete [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

##  <a name="cevent"></a>  CEvent::CEvent

Konstrukce a pojmenované a nepojmenované `CEvent` objektu.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
Při hodnotě TRUE se vlákno pro `CMultilock` nebo `CSingleLock` objektu je povoleno. V opačném případě musíte počkat, všechna vlákna, kteří chtějí přístup k prostředku.

*bManualReset*<br/>
Při hodnotě TRUE Určuje, jestli objekt události je ruční událost, jinak je objekt události automatického událost.

*lpszName*<br/>
Název `CEvent` objektu. Je nutné zadat, pokud se použije objekt přes hranice procesu. Pokud jeho název odpovídá existující událost, konstruktor vytvoří novou `CEvent` objekt, který odkazuje na události s tímto názvem. Pokud název odpovídá existující objekt synchronizace, který není událost, procesu vytváření se nezdaří. Pokud má hodnotu NULL, bude mít název hodnotu null.

*lpsaAttribute*<br/>
Atributy zabezpečení pro objekt události. Úplný popis této struktury viz [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Přístup nebo vydání `CEvent` objektu, vytvořit [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) objektu a volání jeho [Zámek](../../mfc/reference/csinglelock-class.md#lock) a [odemknout](../../mfc/reference/csinglelock-class.md#unlock) Členské funkce.

Chcete-li změnit stav `CEvent` objekt signalizován (vláken nemusíte čekat), volání [SetEvent](#setevent) nebo [PulseEvent](#pulseevent). Nastavit stav `CEvent` objekt nonsignaled (musíte počkat vláken), volání [ResetEvent](#resetevent).

> [!IMPORTANT]
>  Po vytvoření `CEvent` objektu, použijte [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) zajistit, že mutex ještě neexistuje. Pokud mutex neočekávaně neexistuje, může to znamenat podvodný procesu je obsazení a může být úmyslem použít mutex závadně. Doporučený postup zabezpečení v tomto případě je zavřít popisovač a pokračovat, jako při vytváření objektu došlo k chybě.

##  <a name="pulseevent"></a>  CEvent::PulseEvent

Nastaví stav události pro signalizován (k dispozici), verze všech čekajících vláken a vynuluje ji do nonsignaled (není k dispozici) automaticky.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je ruční událost, jsou vydávány všech čekajících vláken, události je nastavena na nonsignaled a `PulseEvent` vrátí. Pokud události je automatické, se uvolní jedno vlákno, události je nastavena na nonsignaled a `PulseEvent` vrátí.

Pokud žádná vlákna čekající nebo žádná vlákna mohou být vydány okamžitě, `PulseEvent` nastaví stav události pro nonsignaled a vrátí.

`PulseEvent` používá základní Win32 `PulseEvent` funkce, která je možné okamžité odebrat ze stavu čekání pomocí volání asynchronní procedury režimu jádra. Proto `PulseEvent` nespolehlivá a by se nemělo používat nové aplikace. Další informace najdete v tématu [PulseEvent funkce](/windows/desktop/api/winbase/nf-winbase-pulseevent).

##  <a name="resetevent"></a>  CEvent::ResetEvent

Nastaví stav události pro nonsignaled až do, explicitně nastaven do signalizovaného podle [SetEvent](#setevent) členskou funkci.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

To způsobí, že všechna vlákna, které chtějí přístup k této události čekání.

Tato členská funkce není používán automatické události.

##  <a name="setevent"></a>  CEvent::SetEvent

Nastaví stav události pro signalizován, uvolnění všech čekajících vláken.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je ruční události, události zůstane až do signalizovaného [ResetEvent](#resetevent) je volána. V tomto případě mohou být vydány více než jedno vlákno. Pokud události je automatické, události zůstane signalizovaného, dokud se neuvolní jedno vlákno. Systém bude nonsignaled pak nastaven stav události. Pokud žádná vlákna čekající, zůstane stav signalizovaného, dokud se neuvolní jedno vlákno.

##  <a name="unlock"></a>  CEvent::Unlock

Verze objektu události.

```
BOOL Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vlákno vlastní objekt události a události se událost automatické; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána vlákna, které aktuálně vlastní událost automatické pro uvolnění poté, co to je všechno, pokud jejich zamknout objekt je možné znovu použít. Pokud zámek objektu není možné znovu použít, tato funkce bude volat zamknout objekt destruktor.

## <a name="see-also"></a>Viz také

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

