---
title: Třída CJumpList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d22fa264f48d3c5b1b6b88db338bc3be45c3f398
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369047"
---
# <a name="cjumplist-class"></a>CJumpList – třída
A `CJumpList` je seznam zástupců zobrazených po klikněte pravým tlačítkem na ikonu na hlavním panelu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CJumpList;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CJumpList::CJumpList](#cjumplist)|Vytvoří `CJumpList` objektu.|  
|[CJumpList:: ~ CJumpList](#cjumplist__~cjumplist)|Zničí `CJumpList` objektu.|  
  
|Název|Popis|  
|----------|-----------------|  
|[CJumpList::AbortList](#abortlist)|Zruší vytváření seznamu transakce bez potvrzení.|  
|[CJumpList::AddDestination](#adddestination)|Přetíženo. Cílový přidá do seznamu.|  
|[CJumpList::AddKnownCategory](#addknowncategory)|Připojí kategorii známé do seznamu.|  
|[CJumpList::AddTask](#addtask)|Přetíženo. Přidá položky kanonický kategorii úloh.|  
|[CJumpList::AddTasks](#addtasks)|Přidá položky kanonický kategorii úloh.|  
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Přidá oddělovač mezi úkoly.|  
|[CJumpList::ClearAll](#clearall)|Odebere všechny úlohy a cíle, které byly přidány do aktuální instancí třídy `CJumpList` dosavadní práce.|  
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Odebere všechny cíle, které byly přidány do aktuální instancí třídy `CJumpList` dosavadní práce.|  
|[CJumpList::CommitList](#commitlist)|Ukončení transakce vytváření seznamu a potvrdí hlášené seznamu k úložišti přidružené (registru v tomto případě.)|  
|[CJumpList::GetDestinationList](#getdestinationlist)|Načte ukazatele rozhraní do cílového seznamu.|  
|[CJumpList::GetMaxSlots](#getmaxslots)|Načte maximální počet položek, včetně kategorie hlavičky, které můžete zobrazit v nabídce cílový volající aplikace.|  
|[CJumpList::GetRemovedItems](#getremoveditems)|Vrátí pole položek, které představují odebrat cíle.|  
|[CJumpList::InitializeList](#initializelist)|Zahájení transakce vytváření seznamu.|  
|[CJumpList::SetAppID](#setappid)|Nastaví Application User Model ID pro seznam, který budou vytvořeny.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxadv.h  
  
##  <a name="_dtorcjumplist"></a>  CJumpList:: ~ CJumpList  
 Zničí `CJumpList` objektu.  
  
```  
~CJumpList();
```  
  
##  <a name="abortlist"></a>  CJumpList::AbortList  
 Zruší vytváření seznamu transakce bez potvrzení.  
  
```  
void AbortList();
```  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody má stejný účinek jako zničení `CJumpList` bez volání `CommitList`.  
  
##  <a name="adddestination"></a>  CJumpList::AddDestination  
 Cílový přidá do seznamu.  
  
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
 `lpcszCategoryName`  
 Určuje název kategorie. Pokud zadaná kategorie neexistuje, bude vytvořen.  
  
 `strDestinationPath`  
 Určuje cestu k cílovému souboru.  
  
 `strCategoryName`  
 Určuje název kategorie. Pokud zadaná kategorie neexistuje, bude vytvořen.  
  
 `pShellItem`  
 Určuje položku prostředí představující cíl, který chcete přidat.  
  
 `pShellLink`  
 Určuje odkaz prostředí představující cíl, který chcete přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Instance `CJumpList` interně shromažďuje přidané cíle a pak je do potvrdí `CommitList`.  
  
##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory  
 Připojí kategorii známé do seznamu.  
  
```  
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```  
  
### <a name="parameters"></a>Parametry  
 `category`  
 Určuje typ známé kategorie. Může být buď `KDC_RECENT`, nebo `KDC_KNOWN`.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Známé kategorie jsou častých a poslední kategorie, které jsme automaticky vypočítá pro každou aplikaci, která využívá `SHAddToRecentDocs` (nebo nepřímo používá jako prostředí bude volat jménem aplikace v některých případech).  
  
##  <a name="addtask"></a>  CJumpList::AddTask  
 Přidá položky kanonický kategorii úloh.  
  
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
 `strTargetExecutablePath`  
 Určuje cílovou cestu úloh.  
  
 `strCommandLineArgs`  
 Určuje argumenty příkazového řádku ke spustitelnému souboru určeného strTargetExecutablePath.  
  
 `strTitle`  
 Název úlohy, která se zobrazí v seznamu cíl.  
  
 `strIconLocation`  
 Umístění ikony, která se zobrazí v seznamu cíl společně s název.  
  
 `iIconIndex`  
 Ikona index.  
  
 `pShellLink`  
 Odkaz prostředí, který představuje přidat úloha.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Instance `CJumpList` shromažďuje zadané úlohy a přidá je do seznamu cíl během `CommitList`. Úloha položky se zobrazí v kategorii v dolní části nabídky cílové aplikace. Tuto kategorii má přednost před všech ostatních kategorií, pokud je vyplněno uživatelského rozhraní.  
  
##  <a name="addtasks"></a>  CJumpList::AddTasks  
 Přidá položky kanonický kategorii úloh.  
  
```  
BOOL AddTasks(IObjectArray* pObjectCollection);
```  
  
### <a name="parameters"></a>Parametry  
 `pObjectCollection`  
 Kolekci úloh má být přidán.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Instanci CJumpList shromažďuje zadané úlohy a přidá je do seznamu cíl během `CommitList`. Úloha položky se zobrazí v kategorii v dolní části nabídky cílové aplikace. Tuto kategorii má přednost před všech ostatních kategorií, pokud je vyplněno uživatelského rozhraní.  
  
##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator  
 Přidá oddělovač mezi úkoly.  
  
```  
BOOL AddTaskSeparator();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je úspěšné, 0, pokud není.  
  
##  <a name="cjumplist"></a>  CJumpList::CJumpList  
 Vytvoří `CJumpList` objektu.  
  
```  
CJumpList(BOOL bAutoCommit = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutoCommit`  
 Pokud má parametr hodnotu FALSE v seznamu není v destruktoru potvrdí automaticky.  
  
##  <a name="clearall"></a>  CJumpList::ClearAll  
 Odebere všechny úlohy a cíle, které byly přidány do aktuální instancí třídy `CJumpList` dosavadní práce.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vymaže a uvolní všechna data a interních rozhraní.  
  
##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations  
 Odebere všechny cíle, které byly přidány do aktuální instancí třídy CJumpList dosavadní práce.  
  
```  
void ClearAllDestinations();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je třeba odebrat všechny cíle, které byly přidány, pokud v aktuální relaci cílového seznamu vytváření a znovu přidejte jiným cílům, volání této funkce. Pokud interní `ICustomDestinationList` byl inicializován, je ponechán zachování připojení.  
  
##  <a name="commitlist"></a>  CJumpList::CommitList  
 Ukončí vytváření seznamu transakce a potvrdí seznamu hlášené přidružené úložiště (v tomto případě registru).  
  
```  
BOOL CommitList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Potvrzení je atomic. Pokud se potvrzení nezdaří, bude vrácena chyba.  Když `CommitList` nazývá aktuální seznam odebrané položky se vyčistí. Voláním této metody znovu nastaví objekt, takže nemá aktivní transakce vytváření seznamu. K aktualizaci seznamu `BeginList` musí být volán znovu.  
  
##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList  
 Načte ukazatele rozhraní do cílového seznamu.  
  
```  
ICustomDestinationList* GetDestinationList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Pokud seznam odkazů nebyla inicializována, nebo byla zapsána nebo přerušena, bude vrácená hodnota `NULL`.  
  
##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots  
 Načte maximální počet položek, včetně kategorie hlavičky, které můžete zobrazit v nabídce cílový volající aplikace.  
  
```  
UINT GetMaxSlots() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Aplikace může hlásit pouze počet položek a kategorie hlavičky kombinaci až tuto hodnotu. Pokud volání `AppendCategory`, `AppendKnownCategory`, nebo `AddUserTasks` přesahovat tento počet, jejich, vrátí hodnotu neúspěch.  
  
##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems  
 Vrátí pole položek, které představují odebrat cíle.  
  
```  
IObjectArray* GetRemovedItems();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Odebrané cíle jsou načteny během inicializace seznamu přechod. Při generování nový cílový seznam, aplikace by měly nejprve zpracovat odebrané seznamu a vymazání svá data sledování pro libovolnou položku vrácený odebrané seznamu enumerátor. Pokud se aplikace pokusí zadejte položku, která byla odebrána pouze v transakci. Toto volání aktuální `BeginList` spustili, volání metody, které znovu přidat daná položka se nepodaří, ujistěte se, že aplikace jsou bere ohledy na seznamu odebrána.  
  
##  <a name="initializelist"></a>  CJumpList::InitializeList  
 Zahájení transakce vytváření seznamu.  
  
```  
BOOL InitializeList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Není nutné explicitně volat tuto metodu, pokud chcete načíst ukazatel na `ICustomDestinationList` pomocí `GetDestinationList`, počet dostupné sloty pomocí `GetMaxSlots`, nebo seznam odebrané položky pomocí `GetRemovedItems`.  
  
##  <a name="setappid"></a>  CJumpList::SetAppID  
 Nastaví Application User Model ID pro seznam, který budou vytvořeny.  
  
```  
void SetAppID(LPCTSTR strAppID);
```  
  
### <a name="parameters"></a>Parametry  
 `strAppID`  
 Řetězec, který určuje ID modelu uživatele aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
