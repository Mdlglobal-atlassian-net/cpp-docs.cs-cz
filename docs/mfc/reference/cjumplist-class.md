---
title: Cjumplist – třída
ms.date: 11/04/2016
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: b72ea6f3715be1e4a11d457dbdeaba7a622ef8b6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259071"
---
# <a name="cjumplist-class"></a>Cjumplist – třída

A `CJumpList` je seznam zástupců zobrazených po klepnutí pravým tlačítkem myši na ikonu na hlavním panelu.

## <a name="syntax"></a>Syntaxe

```
class CJumpList;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Vytvoří `CJumpList` objektu.|
|[CJumpList::~CJumpList](#cjumplist__~cjumplist)|Odstraní `CJumpList` objektu.|

|Název|Popis|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Přeruší transakci sestavování seznamu bez potvrzení.|
|[CJumpList::AddDestination](#adddestination)|Přetíženo. Přidá cílový do seznamu.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Kategorie známé přidá do seznamu.|
|[CJumpList::AddTask](#addtask)|Přetíženo. Přidá položky ke kategorii úkolů canonical.|
|[CJumpList::AddTasks](#addtasks)|Přidá položky ke kategorii úkolů canonical.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Přidá oddělovač mezi úkoly.|
|[CJumpList::ClearAll](#clearall)|Odebere všechny úlohy a cíle, které byly přidány k aktuální instanci `CJumpList` doposud.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Odebere všechny cíle, které byly přidány k aktuální instanci `CJumpList` doposud.|
|[CJumpList::CommitList](#commitlist)|Ukončí vytváření seznamu transakce a potvrzení seznamu ohlášené přidružené úložiště (registru v tomto případě.)|
|[CJumpList::GetDestinationList](#getdestinationlist)|Načte ukazatel rozhraní do cílového seznamu.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Získá maximální počet položek, včetně záhlaví kategorií, které můžete zobrazit v nabídce Cíl volající aplikace.|
|[CJumpList::GetRemovedItems](#getremoveditems)|Vrátí pole položek, které představují odebrat cíle.|
|[CJumpList::InitializeList](#initializelist)|Zahájení sestavování seznamu transakce.|
|[CJumpList::SetAppID](#setappid)|Nastaví ID modelu uživatele aplikace pro seznam, který bude sestaven.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxadv.h

##  <a name="_dtorcjumplist"></a>  CJumpList::~CJumpList

Odstraní `CJumpList` objektu.

```
~CJumpList();
```

##  <a name="abortlist"></a>  CJumpList::AbortList

Přeruší transakci sestavování seznamu bez potvrzení.

```
void AbortList();
```

### <a name="remarks"></a>Poznámky

Voláním této metody má stejný účinek jako zničení `CJumpList` bez volání `CommitList`.

##  <a name="adddestination"></a>  CJumpList::AddDestination

Přidá cílový do seznamu.

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>Parametry

*lpcszCategoryName*<br/>
Určuje název kategorie. Pokud se určené kategorii neexistuje, vytvoří se.

*strDestinationPath*<br/>
Určuje cestu k cílovému souboru.

*strCategoryName*<br/>
Určuje název kategorie. Pokud se určené kategorii neexistuje, vytvoří se.

*pShellItem*<br/>
Určuje položku prostředí představují cílovou přidán.

*pShellLink*<br/>
Určuje odkaz prostředí představují cílovou přidán.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Instance `CJumpList` interně nahromadí přidání cíle a pak je v potvrzení `CommitList`.

##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory

Kategorie známé přidá do seznamu.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Parametry

*Kategorie*<br/>
Určuje typ známé kategorie. Může být KDC_RECENT nebo KDC_KNOWN.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Označuje kategorie jsou časté a poslední kategorie, které jsme se automaticky vypočítat pro každou aplikaci, která využívá `SHAddToRecentDocs` (nebo nepřímo využívá jako prostředí bude volat jménem vaší aplikace v některých případech).

##  <a name="addtask"></a>  CJumpList::AddTask

Přidá položky ke kategorii úkolů canonical.

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>Parametry

*strTargetExecutablePath*<br/>
Určuje cílovou cestu úloh.

*strCommandLineArgs*<br/>
Určuje argumenty příkazového řádku určený strTargetExecutablePath spustitelného souboru.

*strTitle*<br/>
Název úkolu, který se zobrazí v seznamu cíl.

*strIconLocation*<br/>
Umístění ikony, která se zobrazí v seznamu cíl společně s názvem.

*iIconIndex*<br/>
Ikona index.

*pShellLink*<br/>
Odkaz prostředí, který představuje úlohu chcete přidat.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Instance `CJumpList` nahromadí zadané úlohy a přidá je do cílového seznamu během `CommitList`. V kategorii v dolní části nabídky cílové aplikace se zobrazí položky úkolu. Tato kategorie má přednost před všech ostatních kategorií po naplnění v uživatelském rozhraní.

##  <a name="addtasks"></a>  CJumpList::AddTasks

Přidá položky ke kategorii úkolů canonical.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Parametry

*pObjectCollection*<br/>
Kolekce úloh se má přidat.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Instance cjumplist – nahromadí zadané úlohy a přidá je do cílového seznamu během `CommitList`. V kategorii v dolní části nabídky cílové aplikace se zobrazí položky úkolu. Tato kategorie má přednost před všech ostatních kategorií po naplnění v uživatelském rozhraní.

##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator

Přidá oddělovač mezi úkoly.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšné, 0, pokud není.

##  <a name="cjumplist"></a>  CJumpList::CJumpList

Vytvoří `CJumpList` objektu.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoCommit*<br/>
Pokud tento parametr je FALSE seznamu není potvrzena automaticky v destruktoru.

##  <a name="clearall"></a>  CJumpList::ClearAll

Odebere všechny úlohy a cíle, které byly přidány k aktuální instanci `CJumpList` doposud.

```
void ClearAll();
```

### <a name="remarks"></a>Poznámky

Tato metoda vymaže a uvolní všechna data a interní rozhraní.

##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations

Odebere všechny cíle, které byly přidány k aktuální instanci cjumplist – zatím.

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce, pokud je potřeba odebrat všechny cíle, které byly přidány zatím v aktuální relaci cílového seznamu budovy a znovu přidat další weby. Pokud interní `ICustomDestinationList` byl inicializován, že je ponechaný zachování připojení.

##  <a name="commitlist"></a>  CJumpList::CommitList

Ukončí vytváření seznamu transakce a potvrzení seznamu ohlášené přidružené úložiště (v tomto případě registru).

```
BOOL CommitList();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Potvrzení je atomické. Pokud se potvrzení nezdaří, bude vrácena chyba.  Když `CommitList` nazývá aktuální seznam odebrané položky se vymažou. Voláním této metody obnoví objekt tak, že nemá žádné aktivní transakce vytváření seznamu. K aktualizaci seznamu, `BeginList` musí být volána znovu.

##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList

Načte ukazatel rozhraní do cílového seznamu.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Pokud seznam odkazů není inicializovaná, nebo byla potvrzena nebo přerušena, bude vrácenou hodnotou NULL.

##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots

Získá maximální počet položek, včetně záhlaví kategorií, které můžete zobrazit v nabídce Cíl volající aplikace.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Aplikace může jenom nahlásit to počet položek a záhlaví kategorií kombinaci až tuto hodnotu. Pokud volání `AppendCategory`, `AppendKnownCategory`, nebo `AddUserTasks` přesahovat tento počet, se vrátí hodnotu neúspěch.

##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems

Vrátí pole položek, které představují odebrat cíle.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Odebrané cíle jsou načteny během inicializace seznam odkazů. Při generování nového cílového seznamu, aplikace by měly nejprve zpracování seznamu odebrané cíle, vymazat svá data sledování pro všechny položky vrácené odebrané seznam výčtu. Pokud se aplikace pokusí zadat položku, která byla odebrána pouze v transakci, která aktuální volání `BeginList` začít, volání metody, které znovu přidat tuto položku se nezdaří, aby aplikace jsou ale současně zachovává seznamu odebrán.

##  <a name="initializelist"></a>  CJumpList::InitializeList

Zahájení sestavování seznamu transakce.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Není nutné explicitně volat tuto metodu, pokud chcete získat ukazatel na `ICustomDestinationList` pomocí `GetDestinationList`, číslo dostupné sloty pomocí `GetMaxSlots`, nebo seznam odstraněných položek pomocí `GetRemovedItems`.

##  <a name="setappid"></a>  CJumpList::SetAppID

Nastaví ID modelu uživatele aplikace pro seznam, který bude sestaven.

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Parametry

*strAppID*<br/>
Řetězec, který určuje ID modelu uživatele aplikace.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
