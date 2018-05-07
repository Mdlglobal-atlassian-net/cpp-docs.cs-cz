---
title: Služby modelu běhového objektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cff506d559ab44ba4034e982bb909db763917594
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="run-time-object-model-services"></a>Služby modelu běhového objektu
Třídy [CObject](../../mfc/reference/cobject-class.md) a [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) zapouzdření několik služby objektu, včetně přístupu k informacím run-time třída, serializace a vytváření dynamických objektů. Všechny třídy odvozené od `CObject` dědí tuto funkci.  
  
 Přístup k informacím run-time třída umožňuje určit informace o třídě objektu v době běhu. Možnost určit třídu objektu v době běhu je užitečné, pokud budete potřebovat další – kontrola typu argumentů funkce a musíte napsat kód speciální na základě třídy objektu. Run-time třída informace nepodporují přímo jazyka C++.  
  
 Serializace je proces zápisu nebo čtení objektu obsah do nebo ze souboru. Serializace můžete použít k ukládání obsahu objektu i po ukončení aplikace. Objekt lze poté číst ze souboru, když se aplikace restartuje. Tyto objekty dat jsou označeny jako "trvalé."  
  
 Vytváření dynamických objektů můžete vytvořit objekt zadané třídy v době běhu. Například musí podporovat dokumentu, zobrazení a rámečku objekty dynamického vytváření proto rozhraní potřebuje k jejich vytvoření dynamicky.  
  
 Následující tabulka uvádí makry MFC, které podporují run-time třída informace, serializace a dynamického vytváření.  
  
 Další informace o těchto služeb běhového objektu a serializaci, najdete v článku [CObject – třída: informace o třídě přístup k Run-Time](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="run-time-object-model-services-macros"></a>Makra služeb modelu běhového objektu  
  


|||  
|-|-|  
|[DECLARE_DYNAMIC –](#declare_dynamic)|Umožňuje přístup k informacím run-time třída (musí používat v deklaraci třídy).|  
|[DECLARE_DYNCREATE –](#declare_dyncreate)|Umožňuje dynamické vytváření a přístup k informacím run-time třída (musí používat v deklaraci třídy).|  
|[DECLARE_SERIAL –](#declare_serial)|Umožňuje serializace a přístup k informacím run-time třída (musí používat v deklaraci třídy).|  
|[IMPLEMENT_DYNAMIC –](#implement_dynamic)|Umožňuje přístup k informacím run-time třída (musí používat v implementaci třídy).|  
|[IMPLEMENT_DYNCREATE –](#implement_dyncreate)|Umožňuje dynamické vytváření a přístup k informacím o spuštění (musí používat v implementaci třídy).|  
|[IMPLEMENT_SERIAL –](#implement_serial)|Umožňuje serializace a přístup k informacím run-time třída (musí používat v implementaci třídy).|  
|[RUNTIME_CLASS](#runtime_class)|Vrátí `CRuntimeClass` struktura, která odpovídá třídu s názvem.|  


 OLE často vyžaduje dynamického vytváření objektů za běhu. Aplikace serveru OLE například musí být schopen vytvořit OLE – položky dynamicky v reakci na žádost od klienta. Automatizační server podobně, musí být schopen vytvořit položky v reakci na požadavky od klientů automatizace.  
  
 Knihovny Microsoft Foundation Class poskytuje dvě makra konkrétní k OLE.  
  
### <a name="dynamic-creation-of-ole-objects"></a>Dynamické vytváření objektů OLE  

 






|||  
|-|-|  
|[AFX_COMCTL32_IF_EXISTS –](#afx_comctl32_if_exists)|Určuje, zda knihovny běžných ovládacích prvků implementuje zadaný rozhraní API.|
|[AFX_COMCTL32_IF_EXISTS2 –](#afx_comctl32_if_exists2)|Určuje, zda knihovny běžných ovládacích prvků implementuje zadaný rozhraní API.|
|[DECLARE_OLECREATE –](#declare_olecreate)|Umožňuje vytvořit prostřednictvím automatizace OLE objekty.|  
|[DECLARE_OLECTLTYPE –](#declare_olectltype)|Deklaruje **getusertypenameid –** a `GetMiscStatus` členské funkce třídy ovládacího prvku.|
|[DECLARE_PROPPAGEIDS –](#declare_proppageids)|Deklaruje, že ovládacího prvku OLE obsahuje seznam stránek vlastností zobrazíte její vlastnosti.|
|[IMPLEMENT_OLECREATE –](#implement_olecreate)|Umožňuje vytvořit systémem OLE objekty.|  
|[IMPLEMENT_OLECTLTYPE –](#implement_olectltype)|Implementuje **getusertypenameid –** a `GetMiscStatus` členské funkce třídy ovládacího prvku.|  
|[IMPLEMENT_OLECREATE_FLAGS –](#implement_olecreate_flags)|Buď toto makro nebo [implement_olecreate –](#implement_olecreate) musí být v souboru implementace pro třídy, které používá `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS –
Určuje, zda knihovny běžných ovládacích prvků implementuje zadaný rozhraní API.  
   
### <a name="syntax"></a>Syntaxe  
  ```  
AFX_COMCTL32_IF_EXISTS(  proc );  
```
### <a name="parameters"></a>Parametry  
 `proc`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název funkce nebo určuje pořadového čísla funkce. Pokud tento parametr je pořadové hodnoty, musí být v aplikaci word nejnižší; word horní musí být nula. Tento parametr musí být ve formátu Unicode.  
   
### <a name="remarks"></a>Poznámky  
 Použít tento makro k určení, zda knihovnu běžné ovládací prvky funkce určeného `proc` (namísto volání [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212).  
   
### <a name="requirements"></a>Požadavky  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Viz také  
 [Izolace MFC běžné ovládací prvky knihovny](../isolation-of-the-mfc-common-controls-library.md) [afx_comctl32_if_exists2 –](#afx_comctl32_if_exists2)
 
## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2 –
Určuje, zda knihovny běžných ovládacích prvků implementuje zadaný rozhraní API (Toto je verze Unicode [afx_comctl32_if_exists –](#afx_comctl32_if_exists)).  
   
### <a name="syntax"></a>Syntaxe    
```  
AFX_COMCTL32_IF_EXISTS2( proc );  
```
### <a name="parameters"></a>Parametry  
 `proc`  
 Ukazatel na ukončené hodnotou null řetězec obsahující název funkce nebo určuje pořadového čísla funkce. Pokud tento parametr je pořadové hodnoty, musí být v aplikaci word nejnižší; word horní musí být nula. Tento parametr musí být ve formátu Unicode.  
   
### <a name="remarks"></a>Poznámky  
 Použít tento makro k určení, zda knihovnu běžné ovládací prvky funkce určeného `proc` (namísto volání [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212). Toto makro je Unicode verze `AFX_COMCTL32_IF_EXISTS`.  
   
### <a name="requirements"></a>Požadavky  
 afxcomctl32.h, afxcomctl32.inl  
   
### <a name="see-also"></a>Viz také  
 [Izolace MFC běžné ovládací prvky knihovny](../isolation-of-the-mfc-common-controls-library.md) [afx_comctl32_if_exists –](#afx_comctl32_if_exists)



##  <a name="declare_dynamic"></a>  DECLARE_DYNAMIC –  
 Přidá přístup běhu informace o třídě objektu při odvození třídy z `CObject`.  
  
```
DECLARE_DYNAMIC(class_name) 
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
### <a name="remarks"></a>Poznámky  
 Přidat `DECLARE_DYNAMIC` makro modulu hlavičky () pro třídu, pak zahrňte tento modul ve všech modulech sada, kteří potřebují přístup k objektům této třídy.  
  
 Pokud použijete **DECLARE**_ **dynamické** a `IMPLEMENT_DYNAMIC` makra, jak je popsáno, pak můžete použít `RUNTIME_CLASS` makro a `CObject::IsKindOf` funkce určit třídu objektů na spuštění čas.  
  
 Pokud `DECLARE_DYNAMIC` je zahrnuta v deklaraci třídy, pak `IMPLEMENT_DYNAMIC` musí být součástí implementaci třídy.  
  
 Další informace o `DECLARE_DYNAMIC` makro, najdete v části [témata třídy CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [implement_dynamic –](#implement_dynamic).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE –  
 Umožňuje objekty `CObject`-odvozených tříd vytváření dynamicky za běhu.  
  
```
DECLARE_DYNCREATE(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá tato možnost k vytváření nových objektů dynamicky. Například nové zobrazení, vytvoří, když otevřete nový dokument. Dokumentu, zobrazení a rámečku třídy by měly podporovat dynamického vytváření, protože rozhraní potřebuje k jejich vytvoření dynamicky.  
  
 Přidat `DECLARE_DYNCREATE` makro v modulu .h pro třídu, pak zahrňte tento modul ve všech modulech sada, kteří potřebují přístup k objektům této třídy.  
  
 Pokud `DECLARE_DYNCREATE` je zahrnuta v deklaraci třídy, pak `IMPLEMENT_DYNCREATE` musí být součástí implementaci třídy.  
  
 Další informace o `DECLARE_DYNCREATE` makro, najdete v části [témata třídy CObject](../../mfc/using-cobject.md).  
  
> [!NOTE]
>  `DECLARE_DYNCREATE` Makro obsahuje všechny funkce `DECLARE_DYNAMIC`.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [IMPLEMENT_DYNCREATE](#implement_dyncreate).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

 
## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE
Deklaruje **getusertypenameid –** a `GetMiscStatus` členské funkce třídy ovládacího prvku.  
   
### <a name="syntax"></a>Syntaxe    
```
DECLARE_OLECTLTYPE( class_name )  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládacího prvku.  
   
### <a name="remarks"></a>Poznámky  
 **Getusertypenameid –** a `GetMiscStatus` jsou čistá virtuální funkce deklarované v `COleControl`. Protože tyto funkce jsou čistá virtuální, je nutné přepsat ve třídě ovládacího prvku. Kromě **declare_olectltype –**, je nutné přidat `IMPLEMENT_OLECTLTYPE` makro k vaší deklaraci třídy ovládacího prvku.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
   
### <a name="see-also"></a>Viz také  
 [IMPLEMENT_OLECTLTYPE –](#implement_olectltype)
 

## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS
Deklaruje, že ovládacího prvku OLE obsahuje seznam stránek vlastností zobrazíte její vlastnosti.  
   
### <a name="syntax"></a>Syntaxe    
```
DECLARE_PROPPAGEIDS( class_name )  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládacího prvku, který vlastní stránky vlastností.  
   
### <a name="remarks"></a>Poznámky  
 Použití `DECLARE_PROPPAGEIDS` makro na konci deklarace třídy. Potom v souboru sada, která definuje členské funkce pro třídu, použijte `BEGIN_PROPPAGEIDS` makro, makro položky pro všechny stránky vlastností ovládacího prvku a `END_PROPPAGEIDS` makro deklarovat konec seznamu vlastností stránky.  
  
 Další informace o stránky vlastností, najdete v článku [– ovládací prvky ActiveX: stránky vlastností](../mfc-activex-controls-property-pages.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
   
### <a name="see-also"></a>Viz také   
 [BEGIN_PROPPAGEIDS –](#begin_proppageids)   
 [END_PROPPAGEIDS –](#end_proppageids)

##  <a name="declare_serial"></a>  DECLARE_SERIAL –  
 Generuje kód záhlaví C++ potřebné pro `CObject`-odvozené třídy, které lze serializovat.  
  
```
DECLARE_SERIAL(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
### <a name="remarks"></a>Poznámky  
 Serializace je proces zápisu nebo čtení obsah objekt do a ze souboru.  
  
 Použití `DECLARE_SERIAL` makro v modul .h a poté zahrnout Tenhle modul všechny sada moduly, které potřebují přístup k objektům této třídy.  
  
 Pokud `DECLARE_SERIAL` je zahrnuta v deklaraci třídy, pak `IMPLEMENT_SERIAL` musí být součástí implementaci třídy.  
  
 `DECLARE_SERIAL` Makro obsahuje všechny funkce `DECLARE_DYNAMIC` a `DECLARE_DYNCREATE`.  
  
 Můžete použít **AFX_API** makro automaticky exportovat `CArchive` operátor extrakce pro třídy, které používají `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra. Závorka deklarace tříd (nachází se v souboru h) s následujícím kódem:  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Další informace o `DECLARE_SERIAL` makro, najdete v části [témata třídy CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="implement_dynamic"></a>  IMPLEMENT_DYNAMIC –  
 Generuje kód C++ potřebné pro dynamický `CObject`-odvozené třídy s přístupem k spuštění název třídy a pozici v rámci hierarchie.  
  
```
IMPLEMENT_DYNAMIC(class_name, base_class_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
 `base_class_name`  
 Název základní třídy.  
  
### <a name="remarks"></a>Poznámky  
 Použití `IMPLEMENT_DYNAMIC` makro v modulu sada a pak odkaz výsledný objekt kódu pouze jednou.  
  
 Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="implement_dyncreate"></a>  IMPLEMENT_DYNCREATE –  
 Umožňuje objekty `CObject`-odvozených tříd pro dynamicky vytvořen při spuštění čas při použití s `DECLARE_DYNCREATE` makro.  
  
```
IMPLEMENT_DYNCREATE(class_name, base_class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
 `base_class_name`  
 Skutečný název základní třídy.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá tato možnost k vytváření nových objektů dynamicky, například při čtení objektu z disku během serializace. Přidat `IMPLEMENT_DYNCREATE` makro v souboru implementace třídy. Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).  
  
 Pokud použijete `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE` makra, pak můžete použít `RUNTIME_CLASS` makro a `CObject::IsKindOf` – členská funkce určit třídu objektů za běhu.  
  
 Pokud `DECLARE_DYNCREATE` je zahrnuta v deklaraci třídy, pak `IMPLEMENT_DYNCREATE` musí být součástí implementaci třídy.  
  
 Všimněte si, že tuto definici makra vyvolá pro třídu výchozí konstruktor. Pokud nejsou v netriviálních konstruktor je explicitně implementované třídu, musí také výslovně implementovat výchozí konstruktor. Výchozí konstruktor lze přidat na třídu **privátní** nebo **chráněné** člen části zabráníte volána z mimo implementaci třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]  
  
 [!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

## <a name="implement_olecreate_flags"></a>  IMPLEMENT_OLECREATE_FLAGS –
Buď toto makro nebo [implement_olecreate –](#implement_olecreate) musí být v souboru implementace pro třídy, které používá `DECLARE_OLECREATE`.  
   
### <a name="syntax"></a>Syntaxe    
```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags, 
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
 *external_name*  
 Název objektu zveřejněné k ostatním aplikacím (uzavřena v uvozovkách).  
  
 `nFlags`  
 Obsahuje jeden nebo více z následujících příznaků:  
  
-   `afxRegInsertable` Umožňuje zobrazit v dialogovém okně Vložit objekt pro objekty OLE.    
-   `afxRegApartmentThreading` Nastaví v registru na ThreadingModel model vláken typu Apartment =.    
-   **afxregfreethreading –** nastaví model vláken v registru na ThreadingModel = volné.  
  
     Dvěma příznaky můžete kombinovat `afxRegApartmentThreading` a `afxRegFreeThreading` nastavit ThreadingModel = obě. V tématu [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) ve Windows SDK pro další informace o dělení na vlákna registrace modelu.    
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8*  
 Součástí třída **CLSID**.  
   
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud používáte `IMPLEMENT_OLECREATE_FLAGS`, můžete určit, které modelu vláken objektu podporuje pomocí `nFlags` parametr. Pokud chcete podporovat pouze jeden chůze model, použijte `IMPLEMENT_OLECREATE`.  
  
 Externí název je identifikátor zpřístupnit jiným aplikacím. Klientské aplikace používají k požadavku na tato třída objektu ze serveru automatizace externí název.  
  
 ID třídy OLE je jedinečný identifikátor 128-bit pro objekt. Se skládá z jednoho **dlouho**, dvě **WORD**s a osm **BAJTŮ**s reprezentovaná *l*, *w1*, *w2*, a *b1* prostřednictvím *b8* v popisu syntaxe. Průvodce vytvořením aplikace a kód průvodců pro vás vytvořil jedinečné ID tříd OLE podle potřeby.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [DECLARE_OLECREATE –](#declare_olecreate)   
 [Klíč CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424)


## <a name="implement_olecreate"></a> IMPLEMENT_OLECTLTYPE –
Implementuje **getusertypenameid –** a `GetMiscStatus` členské funkce třídy ovládacího prvku.  
   
### <a name="syntax"></a>Syntaxe    
```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )  
```
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládacího prvku.  
  
 *idsUserTypeName*  
 ID prostředku řetězec obsahující externí název ovládacího prvku.  
  
 *dwOleMisc*  
 Výčet obsahující jeden nebo více příznaků. Další informace o tento výčet najdete v tématu [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) ve Windows SDK.  
   
### <a name="remarks"></a>Poznámky  
 Kromě `IMPLEMENT_OLECTLTYPE`, je nutné přidat **declare_olectltype –** makro k vaší deklaraci třídy ovládacího prvku.  
  
 **Getusertypenameid –** – členská funkce vrátí řetězec prostředku, který identifikuje třídě ovládacího prvku. `GetMiscStatus` Vrátí **OLEMISC** bits pro ovládací prvek. Tento výčet určuje kolekce nastavení, které popisují různé vlastnosti ovládacího prvku. Úplný popis **OLEMISC** najdete v části nastavení, [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) ve Windows SDK.  
  
> [!NOTE]
>  Výchozí nastavení používané ActiveX ControlWizard: **OLEMISC_ACTIVATEWHENVISIBLE**, **OLEMISC_SETCLIENTSITEFIRST**, **OLEMISC_INSIDEOUT**, **OLEMISC_CANTLINKINSIDE**, a **OLEMISC_RECOMPOSEONRESIZE**.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [DECLARE_OLECTLTYPE –](#declare_olectltype)

##  <a name="implement_serial"></a>  IMPLEMENT_SERIAL –  
 Generuje kód C++ potřebné pro dynamický `CObject`-odvozené třídy s přístupem k spuštění název třídy a pozici v rámci hierarchie.  
  
```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
 `base_class_name`  
 Název základní třídy.  
  
 *wSchema*  
 A **Celé_číslo** "číslo verze", který bude zakódován v archivu povolit deserializaci program k identifikaci a zpracovat data vytvořená starší verze programu. Číslo schéma třídy nesmí mít hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
 Použití `IMPLEMENT_SERIAL` makro v modulu sada; pak propojit výsledný objekt kódu pouze jednou.  
  
 Můžete použít **AFX_API** makro automaticky exportovat `CArchive` operátor extrakce pro třídy, které používají `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra. Závorka deklarace tříd (nachází se v souboru h) s následujícím kódem:  
  
 [!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]  
  
 Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="runtime_class"></a>  RUNTIME_CLASS  
 Získá strukturu run-time třída z název třídy C++.  
  
```
RUNTIME_CLASS(class_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy (není uzavřena v uvozovkách).  
  
### <a name="remarks"></a>Poznámky  
 `RUNTIME_CLASS` vrátí ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury určeného třída *class_name*. Pouze `CObject`-odvozených třídách deklarovat s `DECLARE_DYNAMIC`, `DECLARE_DYNCREATE`, nebo `DECLARE_SERIAL` vrátí ukazatele na `CRuntimeClass` struktury.  
  
 Další informace najdete v tématu [témata třídy CObject](../../mfc/using-cobject.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 
   
##  <a name="declare_olecreate"></a>  DECLARE_OLECREATE –  
 Umožňuje objekty `CCmdTarget`-odvozených tříd, které mají být vytvořeny prostřednictvím automatizace OLE.  
  
```
DECLARE_OLECREATE(class_name) 
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro umožňuje dalších aplikací s povolenými OLE k vytváření objektů tohoto typu.  
  
 Přidat `DECLARE_OLECREATE` makro v modulu .h pro třídu a poté zahrnout Tenhle modul všechny sada moduly, které potřebují přístup k objektům této třídy.  
  
 Pokud `DECLARE_OLECREATE` je zahrnuta v deklaraci třídy, pak `IMPLEMENT_OLECREATE` musí být součástí implementaci třídy. Deklarace třídy pomocí `DECLARE_OLECREATE` musíte také použít `DECLARE_DYNCREATE` nebo `DECLARE_SERIAL`.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h  

##  <a name="implement_olecreate"></a>  IMPLEMENT_OLECREATE –  
 Buď toto makro nebo [implement_olecreate_flags –](#implement_olecreate_flags) musí být v souboru implementace pro třídy, které používá `DECLARE_OLECREATE`.  
  
```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Skutečný název třídy.  
  
 *external_name*  
 Název objektu zveřejněné k ostatním aplikacím (uzavřena v uvozovkách).  
  
 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8*  
 Součástí třída **CLSID**.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pokud používáte `IMPLEMENT_OLECREATE`, ve výchozím nastavení, které podporujete jenom jeden model vláken. Pokud používáte `IMPLEMENT_OLECREATE_FLAGS`, můžete určit, které modelu vláken objektu podporuje pomocí `nFlags` parametr.  
  
 Externí název je identifikátor zpřístupnit jiným aplikacím. Klientské aplikace používají k požadavku na tato třída objektu ze serveru automatizace externí název.  
  
 ID třídy OLE je jedinečný identifikátor 128-bit pro objekt. Se skládá z jednoho **dlouho**, dvě **WORD**s a osm **BAJTŮ**s reprezentovaná *l*, *w1*, *w2*, a *b1* prostřednictvím *b8* v popisu syntaxe. Průvodce vytvořením aplikace a kód průvodců pro vás vytvořil jedinečné ID tříd OLE podle potřeby.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví**: afxdisp.h 

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)

