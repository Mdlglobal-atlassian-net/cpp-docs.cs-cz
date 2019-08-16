---
title: CMultiLock Class
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: b2fe3ecf2197b8edb13e89600b16e550deff9af2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504539"
---
# <a name="cmultilock-class"></a>CMultiLock Class

Představuje mechanismus pro řízení přístupu, který se používá při řízení přístupu k prostředkům v programu s více vlákny.

## <a name="syntax"></a>Syntaxe

```
class CMultiLock
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|`CMultiLock` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMultiLock::-lockd](#islocked)|Určuje, zda je určitý objekt synchronizace v poli uzamčen.|
|[CMultiLock::Lock](#lock)|Počká na pole synchronizačních objektů.|
|[CMultiLock:: Unlock](#unlock)|Uvolňuje všechny vlastněné objekty synchronizace.|

## <a name="remarks"></a>Poznámky

`CMultiLock`nemá základní třídu.

Chcete-li použít synchronizační třídy [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)a [CEvent](../../mfc/reference/cevent-class.md), můžete vytvořit `CMultiLock` objekt nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) , který bude čekat a uvolnit objekt synchronizace. Použijte `CMultiLock` v případě, že existuje více objektů, které lze použít v určitou dobu. Použijte `CSingleLock` , pokud potřebujete počkat jenom na jeden objekt v jednom okamžiku.

Chcete-li `CMultiLock` použít objekt, nejprve vytvořte pole objektů synchronizace, na které chcete čekat. Dále zavolejte `CMultiLock` konstruktor objektu uvnitř členské funkce ve třídě kontrolovaného prostředku. Pak zavolejte členskou funkci [zámku](#lock) , abyste zjistili, jestli je prostředek k dispozici (signalizace). Pokud je jedna, pokračujte zbývající částí členské funkce. Pokud není k dispozici žádný prostředek, počkejte na určenou dobu, než se prostředek uvolní, nebo vraťte chybu. Po použití prostředku zavolejte funkci [Unlock](#unlock) , pokud `CMultiLock` se má objekt znovu použít `CMultiLock` , nebo umožněte zničení objektu.

`CMultiLock`objekty jsou nejužitečnější, pokud má vlákno velký počet `CEvent` objektů, na které může reagovat. Vytvořte pole obsahující všechny `CEvent` ukazatele a zavolejte. `Lock` Tím dojde k tomu, že vlákno počká, dokud nebude signalizována jedna z událostí.

Další informace o použití `CMultiLock` objektů naleznete v článku [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CMultiLock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt. h

##  <a name="cmultilock"></a>CMultiLock::CMultiLock

`CMultiLock` Vytvoří objekt.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*ppObjects*<br/>
Pole ukazatelů na objekty synchronizace, které mají být očekávány. Nemůže mít hodnotu NULL.

*dwCount*<br/>
Počet objektů v *ppObjects*. Musí být větší než 0.

*bInitialLock*<br/>
Určuje, zda se má zpočátku pokusit o přístup k libovolnému z dodaných objektů.

### <a name="remarks"></a>Poznámky

Tato funkce je volána po vytvoření pole synchronizačních objektů, které mají být očekávány. Obvykle se volá z vlákna, které musí čekat na zpřístupnění některého z objektů synchronizace.

##  <a name="islocked"></a>CMultiLock::-lockd

Určuje, zda je zadaný objekt nesignálný (není k dispozici).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parametry

*dwItem*<br/>
Index v poli objektů odpovídajících objektu, jehož stav je dotazován.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zadaný objekt uzamčen; v opačném případě 0.

##  <a name="lock"></a>CMultiLock:: Lock

Voláním této funkce získáte přístup k jednomu nebo více prostředkům řízeným synchronizačními objekty dodanými do `CMultiLock` konstruktoru.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Určuje dobu, po kterou se má čekat, než bude objekt synchronizace k dispozici (signalizace). Pokud je nekonečné `Lock` , počká, až bude objekt před vrácením signalizována.

*bWaitForAll*<br/>
Určuje, zda všechny objekty, které se budou čekat, se musí nacházet ve stejné době, než se vrátí. Pokud má hodnotu `Lock` false, vrátí se, pokud některý z objektů čeká na signál.

*dwWakeMask*<br/>
Určuje další podmínky, které mají povolené přerušení čekání. Úplný seznam dostupných možností pro tento parametr naleznete v tématu [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

V `Lock` případě chyby vrátí hodnotu-1. V případě úspěchu vrátí jednu z následujících hodnot:

- Mezi WAIT_OBJECT_0 a WAIT_OBJECT_0 + (počet objektů-1)

   Pokud má *bWaitForAll* hodnotu true, všechny objekty jsou signalizace (k dispozici). Pokud je *BWAITFORALL* false, vrácený Value-WAIT_OBJECT_0 je index v poli objektů objektu, který je signalizace (k dispozici).

- WAIT_OBJECT_0 + (počet objektů)

   Událost zadaná v *dwWakeMask* je k dispozici ve vstupní frontě vlákna.

- Mezi WAIT_ABANDONED_0 a WAIT_ABANDONED_0 + (počet objektů-1)

   Pokud má *bWaitForAll* hodnotu true, všechny objekty jsou signalizace a nejméně jeden z objektů je opuštěným objektem mutex. Pokud je *BWAITFORALL* false, návratová hodnota-WAIT_ABANDONED_0 je index v poli objektů objektu opuštěné mutex, který splnil čekání.

- WAIT_TIMEOUT

   Časový limit zadaný v *dwTimeOut* vyprší bez úspěšného čekání.

### <a name="remarks"></a>Poznámky

Pokud má *bWaitForAll* hodnotu true `Lock` , vrátí se úspěšně, jakmile se všechny synchronizační objekty budou signalizovat současně. Pokud má *bWaitForAll* hodnotu false `Lock` , vrátí se, jakmile se jeden nebo více synchronizačních objektů přestane signalizovat.

Pokud `Lock` se nemůže vrátit hned, počká na to, že nepřekračuje počet milisekund zadaných v parametru *dwTimeOut* , než se vrátí. Pokud je *dwTimeOut* nekonečno, nevrátí se, `Lock` dokud nebude získán přístup k objektu nebo pokud byla splněna podmínka zadaná v *dwWakeMask* . V opačném `Lock` případě, pokud bylo možné získat synchronizační objekt, vrátí se úspěšně. Pokud ne, vrátí se chyba.

##  <a name="unlock"></a>CMultiLock:: Unlock

Uvolní synchronizační objekt vlastněný nástrojem `CMultiLock`.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Počet odkazů, které se mají vydávat Musí být větší než 0. Pokud by zadaná hodnota způsobila překročení maximálního počtu objektů, počet se nemění a funkce vrátí hodnotu FALSE.

*lPrevCount*<br/>
Odkazuje na proměnnou, aby získala předchozí počet pro objekt synchronizace. Pokud má hodnotu NULL, předchozí počet se nevrátí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla funkce úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je volána `CMultiLock`destruktorem.

První tvar `Unlock` se pokusí odemknout synchronizační objekt, který `CMultiLock`spravuje. Druhá forma `Unlock` se pokusí `CSemaphore` odemknout objekty, které vlastní `CMultiLock`. Pokud `CMultiLock` objekt není vlastníkem žádného `CSemaphore` uzamčeného objektu, vrátí funkce hodnotu false. v opačném případě vrátí hodnotu true. *lCount* a *lpPrevCount* jsou přesně stejné jako parametry [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock). Druhá forma z `Unlock` je zřídka platná pro případy s více zámky.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)
