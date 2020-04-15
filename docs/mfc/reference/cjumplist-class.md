---
title: CJumpList – třída
ms.date: 03/27/2019
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
ms.openlocfilehash: 98d6bec3d33c9060ebb741111dff793f64cc7cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372336"
---
# <a name="cjumplist-class"></a>CJumpList – třída

A `CJumpList` je seznam zkratek, které byly odhaleny, když kliknete pravým tlačítkem myši na ikonu na hlavním panelu.

## <a name="syntax"></a>Syntaxe

```
class CJumpList;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Vytvoří `CJumpList` objekt.|
|[CJumpList::~CJumpList](#_dtorcjumplist)|Zničí `CJumpList` objekt.|

|Name (Název)|Popis|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Přeruší transakci vytváření seznamu bez potvrzení.|
|[CJumpList::PřidatCíl](#adddestination)|Přetíženo. Přidá cíl do seznamu.|
|[CJumpList::Přidatkategorii](#addknowncategory)|Připojí známé kategorie do seznamu.|
|[CJumpList::Přidat úkol](#addtask)|Přetíženo. Přidá položky do kategorie kanonické úkoly.|
|[CJumpList::Přidat úkoly](#addtasks)|Přidá položky do kategorie kanonické úkoly.|
|[CJumpList::Oddělovač úloh AddTask](#addtaskseparator)|Přidá oddělovač mezi úkoly.|
|[CJumpList::ClearAll](#clearall)|Odebere všechny úkoly a cíle, které `CJumpList` byly dosud přidány do aktuální instance.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Odebere všechny cíle, které byly dosud přidány do aktuální instance. `CJumpList`|
|[CJumpList::CommitList](#commitlist)|Ukončí transakci vytváření seznamu a potvrdí ohlášený seznam do přidruženého úložiště (v tomto případě do registru).)|
|[CJumpList::GetDestinationList](#getdestinationlist)|Načte ukazatel rozhraní do cílového seznamu.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Načte maximální počet položek, včetně záhlaví kategorií, které lze zobrazit v cílové nabídce volající aplikace.|
|[CJumpList::GetremovedItems](#getremoveditems)|Vrátí pole položek, které představují odebrané cíle.|
|[CJumpList::InitializeList](#initializelist)|Zahájí transakci vytváření seznamu.|
|[CJumpList::SetAppID](#setappid)|Nastaví ID modelu uživatele aplikace pro seznam, který bude sestaven.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxadv.h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>CJumpList::~CJumpList

Zničí `CJumpList` objekt.

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a>CJumpList::AbortList

Přeruší transakci vytváření seznamu bez potvrzení.

```
void AbortList();
```

### <a name="remarks"></a>Poznámky

Volání této metody má stejný `CJumpList` účinek `CommitList`jako zničení bez volání .

## <a name="cjumplistadddestination"></a><a name="adddestination"></a>CJumpList::PřidatCíl

Přidá cíl do seznamu.

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

*lpcszNázev kategorie*<br/>
Určuje název kategorie. Pokud zadaná kategorie neexistuje, bude vytvořena.

*trasa strDestination*<br/>
Určuje cestu k cílovému souboru.

*strCategoryName*<br/>
Určuje název kategorie. Pokud zadaná kategorie neexistuje, bude vytvořena.

*položka pShellItem*<br/>
Určuje položku prostředí představující přidaný cíl.

*pShellLink*<br/>
Určuje odkaz prostředí představující přidávaný cíl.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Instance `CJumpList` interně akumuluje přidané cíle `CommitList`a pak je potvrdí v .

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a>CJumpList::Přidatkategorii

Připojí známé kategorie do seznamu.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Parametry

*Kategorie*<br/>
Určuje známý typ kategorie. Může být buď KDC_RECENT, nebo KDC_KNOWN.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Známé kategorie jsou časté a nedávné kategorie, které budeme `SHAddToRecentDocs` automaticky vypočítat pro každou aplikaci, která využívá (nebo nepřímo používá jako prostředí bude volat jménem aplikace v některých scénářích).

## <a name="cjumplistaddtask"></a><a name="addtask"></a>CJumpList::Přidat úkol

Přidá položky do kategorie kanonické úkoly.

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
Určuje cestu cílového úkolu.

*strCommandLineArgs*<br/>
Určuje argumenty příkazového řádku spustitelného souboru určeného *strTargetExecutablePath*.

*strTitle*<br/>
Název úkolu, který se zobrazí v cílovém seznamu.

*strIconLocation*<br/>
Umístění ikony, která se zobrazí v cílovém seznamu spolu s názvem.

*iIconIndex*<br/>
Index ikon.

*pShellLink*<br/>
Shell Link, který představuje úkol, který má být přidán.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Instance `CJumpList` shromažďuje zadané úkoly a přidává je `CommitList`do cílového seznamu během . Položky úkolů se zobrazí v kategorii v dolní části cílové nabídky aplikace. Tato kategorie má přednost před všemi ostatními kategoriemi při vyplnění v unovém uj.

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a>CJumpList::Přidat úkoly

Přidá položky do kategorie kanonické úkoly.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Parametry

*pObjectCollection*<br/>
Kolekce úkolů, které mají být přidány.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Instance CJumpList akumuluje zadané úkoly a `CommitList`přidá je do cílového seznamu během . Položky úkolů se zobrazí v kategorii v dolní části cílové nabídky aplikace. Tato kategorie má přednost před všemi ostatními kategoriemi při vyplnění v unovém uj.

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>CJumpList::Oddělovač úloh AddTask

Přidá oddělovač mezi úkoly.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, 0, pokud není.

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a>CJumpList::CJumpList

Vytvoří `CJumpList` objekt.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutomatické potvrzení*<br/>
Pokud je tento parametr FALSE, seznam není automaticky potvrzen v destruktoru.

## <a name="cjumplistclearall"></a><a name="clearall"></a>CJumpList::ClearAll

Odebere všechny úkoly a cíle, které `CJumpList` byly dosud přidány do aktuální instance.

```
void ClearAll();
```

### <a name="remarks"></a>Poznámky

Tato metoda vymaže a uvolní všechna data a vnitřní rozhraní.

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>CJumpList::ClearAllDestinations

Odebere všechny cíle, které byly dosud přidány do aktuální instance CJumpList.

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte, pokud potřebujete odebrat všechny cíle, které byly dosud přidány v aktuální relaci vytváření seznamu cílů, a znovu přidat další cíle. Pokud byl `ICustomDestinationList` vnitřní inicializován, zůstane naživu.

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a>CJumpList::CommitList

Ukončí transakci vytváření seznamu a potvrdí ohlášený seznam do přidruženého úložiště (v tomto případě registru).

```
BOOL CommitList();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Potvrzení je atomové. Pokud se potvrzení nezdaří, bude vrácena chyba.  Při `CommitList` volání bude aktuální seznam odebraných položek vyčištěn. Volání této metody obnoví objekt tak, aby nemá aktivní transakce vytváření seznamu. Chcete-li aktualizovat `BeginList` seznam, je třeba zavolat znovu.

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>CJumpList::GetDestinationList

Načte ukazatel rozhraní do cílového seznamu.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Pokud seznam odkazů nebyl inicializován nebo byl potvrzen nebo přerušen, bude vrácená hodnota null.

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a>CJumpList::GetMaxSlots

Načte maximální počet položek, včetně záhlaví kategorií, které lze zobrazit v cílové nabídce volající aplikace.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Aplikace mohou vykazovat pouze počet položek a záhlaví kategorií dohromady až do této hodnoty. Pokud volání `AppendCategory` `AppendKnownCategory`, `AddUserTasks` , nebo překročit toto číslo, vrátí selhání.

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a>CJumpList::GetremovedItems

Vrátí pole položek, které představují odebrané cíle.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Odebrané cíle jsou načteny během inicializace seznamu odkazů. Při generování nového seznamu cílů se očekává, že aplikace nejprve zpracují seznam odebrané cíle a vymažou data sledování pro všechny položky vrácené odebráním čítačem seznamu seznamu. Pokud se aplikace pokusí poskytnout položku, která byla právě odebrána v transakci, kterou bylo `BeginList` spuštěno aktuální volání, volání metody, která tuto položku znovu přidala, se nezdaří, aby bylo zajištěno, že aplikace respektují odstraněný seznam.

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a>CJumpList::InitializeList

Zahájí transakci vytváření seznamu.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Tuto metodu není nutné volat explicitně, pokud nechcete načíst ukazatel na `ICustomDestinationList` použití `GetDestinationList`, počet dostupných slotů používajících `GetMaxSlots`nebo seznam odebraných položek pomocí `GetRemovedItems`.

## <a name="cjumplistsetappid"></a><a name="setappid"></a>CJumpList::SetAppID

Nastaví ID modelu uživatele aplikace pro seznam, který bude sestaven.

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Parametry

*strAppID*<br/>
Řetězec, který určuje ID modelu uživatele aplikace.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
