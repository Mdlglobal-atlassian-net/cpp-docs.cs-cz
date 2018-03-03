---
title: "CObject – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
dev_langs:
- C++
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0384392d42196e4365c59670537819435ce1e45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cobject-class"></a>CObject – třída
Hlavní základní třída pro knihovny Microsoft Foundation Class.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CObject::CObject](#cobject)|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CObject::AssertValid](#assertvalid)|Ověří integritu tohoto objektu.|  
|[CObject::Dump](#dump)|Vytvoří výpis diagnostiky tohoto objektu.|  
|[CObject::GetRuntimeClass](#getruntimeclass)|Vrátí `CRuntimeClass` struktura odpovídající třída tohoto objektu.|  
|[CObject::IsKindOf](#iskindof)|Testy relace tohoto objektu do dané třídy.|  
|[CObject::IsSerializable](#isserializable)|Otestuje, zda tento objekt můžete serializovat.|  
|[CObject::Serialize](#serialize)|Načte nebo uloží objekt z/do archivu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Odstranění CObject::operator](#operator_delete)|Speciální **odstranit** operátor.|  
|[CObject::operator nový](#operator_new)|Speciální **nové** operátor.|  
  
## <a name="remarks"></a>Poznámky  
 Slouží jako kořenový nejen pro knihovny tříd jako `CFile` a `CObList`, ale také pro třídy, které můžete psát. `CObject`poskytuje základní služby, včetně  
  
-   Podpora serializace  
  
-   Informace o run-time třída  
  
-   Výstup diagnostiky objektu  
  
-   Kompatibilita s třídy kolekce  
  
 Všimněte si, že `CObject` nepodporuje vícenásobná dědičnost. Odvozené třídy může mít jen jeden `CObject` základní třídy a že `CObject` musí být krajní levé v hierarchii. Je přípustné, ale tak, aby měl struktury a bez- `CObject`-odvozených tříd v pravém větví vícenásobné dědičnosti.  
  
 Zjistíte hlavní výhody z `CObject` odvození Pokud použijete některé volitelné makra v implementaci třídy a deklarace.  
  
 Makra první úrovně [DECLARE_DYNAMIC –](run-time-object-model-services.md#declare_dynamic) a [implement_dynamic –](run-time-object-model-services.md#implement_dynamic), povolení přístupu běhu název třídy a pozici v hierarchii. To, zase umožňuje smysluplný vypsání diagnostiky.  
  
 Makra druhé úrovně [declare_serial –](run-time-object-model-services.md#declare_serial) a [implement_serial –](run-time-object-model-services.md#implement_serial), zahrnout všechny funkce makra první úrovně, a umožňují objekt tak, aby "serializovat" do a z "archivu".  
  
 Informace o obecně odvozování Microsoft Foundation třídy a třídy jazyka C++ a pomocí `CObject`, najdete v části [pomocí CObject](../../mfc/using-cobject.md) a [serializace](../../mfc/serialization-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="assertvalid"></a>CObject::AssertValid  
 Ověří integritu tohoto objektu.  
  
```  
virtual void AssertValid() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AssertValid`provádí kontroly platnosti na tento objekt kontrolou stavu interní. V ladicí verzi knihovny `AssertValid` může assert a ukončení programu s zprávou, která uvádí, číslo řádku a název souboru, ve kterých selhaly kontrolní výraz.  
  
 Když píšete vlastní třídu, by měly přepsat `AssertValid` funkce poskytovat diagnostiky pro vy a ostatní uživatelé vaší třídy. Přepsané `AssertValid` obvykle volá `AssertValid` funkce její základní třída před zaškrtnutím datových členů, které jsou jedinečné pro odvozené třídy.  
  
 Protože `AssertValid` je **const** funkce, byl odepřen. Chcete-li změnit stav objektu během testu. Vlastní odvozené třídy `AssertValid` funkce nesmí generování výjimek, ale spíše by měl assert zda zjistí neplatný objekt data.  
  
 Definice "platnosti" závisí na třídě objektu. Platí pravidlo funkce měli kontrolu "bez podstruktury." To znamená pokud objekt obsahuje odkazy na jiné objekty, se musí zkontrolujte, zda následující ukazatele nejsou null, ale neměli provést platnosti testování na objekty, na kterou odkazuje následující ukazatele.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
 Jiný příklad najdete v tématu [afxdoforallobjects –](diagnostic-services.md#afxdoforallobjects).  
  
##  <a name="cobject"></a>CObject::CObject  
 Tyto funkce jsou standardní `CObject` konstruktory.  
  
```  
CObject();  
CObject(const CObject& objectSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *objectSrc*  
 Odkaz na jiný`CObject`  
  
### <a name="remarks"></a>Poznámky  
 Výchozí verze je automaticky volána konstruktoru odvozené třídy.  
  
 Pokud je vaše třída serializovatelný (její součástí jsou `IMPLEMENT_SERIAL` makro), pak musí mít výchozí konstruktor (konstruktor bez argumentů) ve vaší deklaraci třídy. Pokud není nutné výchozí konstruktor, deklarovat privátního nebo chráněný "prázdný" konstruktor. Další informace najdete v tématu [pomocí CObject](../../mfc/using-cobject.md).  
  
 Standardní C++ výchozí třídy kopie konstruktor nemá kopii člena člena. Přítomnost privátní `CObject` kopírovacího konstruktoru zaručuje chybová zpráva kompilátoru, pokud je konstruktor copy vaší třídy potřebných ale není k dispozici. Proto je nutné zadat kopírovacího konstruktoru, pokud tato možnost vyžaduje, aby třídě.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>CObject::Dump  
 Vypíše obsah vašeho objektu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objektu.  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dc`  
 Kontext diagnostiky výpis pro vypsání obvykle `afxDump`.  
  
### <a name="remarks"></a>Poznámky  
 Když píšete vlastní třídu, by měly přepsat `Dump` funkce poskytovat diagnostiky pro vy a ostatní uživatelé vaší třídy. Přepsané `Dump` obvykle volá `Dump` funkce její základní třída před tiskem datových členů, které jsou jedinečné pro odvozené třídy. `CObject::Dump`Zobrazí název třídy, pokud používá třídu `IMPLEMENT_DYNAMIC` nebo `IMPLEMENT_SERIAL` makro.  
  
> [!NOTE]
>  Vaše `Dump` funkce nesmí tisku znak nového řádku na konci její výstup.  
  
 `Dump`volání smysl pouze v ladicí verzi knihovny Microsoft Foundation Class. Měli závorka volání, deklarace funkce a funkce implementace s **_DEBUG #ifdef –** /  `#endif` příkazy pro Podmíněná kompilace.  
  
 Vzhledem k tomu `Dump` je **const** funkce, byl odepřen. Chcete-li změnit stav objektu při výpisu.  
  
 [CDumpContext vložení (<<) operátor](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) volání `Dump` při `CObject` je vložen ukazatele.  
  
 `Dump`povoluje pouze "Acyklické" vypsání objektů. Je možné vypsat seznam objektů, například, ale pokud některý z objektů v seznamu sám sebe, bude nakonec přetečení zásobníku.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>CObject::GetRuntimeClass  
 Vrátí `CRuntimeClass` struktura odpovídající třída tohoto objektu.  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura odpovídající tento objekt třídy; nikdy **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Existuje `CRuntimeClass` strukturu pro každý `CObject`-odvozené třídy. Členové struktury jsou následující:  
  
- **LPCSTR m_lpszClassName** ukončené hodnotou null řetězec obsahující název třídy ASCII.  
  
- **int m_nObjectSize** velikost objektu v bajtech. Pokud objekt má datových členů, které odkazují na přidělenou paměť, velikost paměti, že není součástí.  
  
- **UINT m_wSchema** číslo schématu (-1 pro třídy nonserializable). Najdete v článku [implement_serial –](run-time-object-model-services.md#implement_serial) makro popis číslo schématu.  
  
- **CObject\* (PASCAL\* m_pfnCreateObject) ()** ukazatel funkce na výchozí konstruktor, který vytvoří objekt vaší třídy (platná pouze v případě, že třída podporuje dynamické vytvoření; jinak vrátí **hodnotu NULL.** ).  
  
- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** Pokud vaše aplikace je dynamicky propojené s AFXDLL – verze knihovny MFC, ukazatel na funkci, která vrací `CRuntimeClass` struktura základní třídy.  
  
- **CRuntimeClass\* m_pBaseClass** Pokud vaše aplikace je staticky propojené do MFC, odkazy `CRuntimeClass` struktura základní třídy.  
  
 Tato funkce vyžaduje použití [implement_dynamic –](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), nebo [implement_serial –](run-time-object-model-services.md#implement_serial) makro v implementaci třídy. V opačném případě obdržíte nesprávné výsledky.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>CObject::IsKindOf  
 Testy relace tohoto objektu do dané třídy.  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pClass`  
 Ukazatel na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura přidružené k vaší `CObject`-odvozené třídy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt odpovídá třídy; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce testy `pClass` zda (1) je objekt pro zadanou třídu nebo (2) je objekt třídy odvozené od pro zadanou třídu. Tato funkce funguje pouze pro třídy deklarovat s [DECLARE_DYNAMIC –](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE –](run-time-object-model-services.md#declare_dyncreate), nebo [declare_serial –](run-time-object-model-services.md#declare_serial) makro.  
  
 Nepoužívejte tuto funkci hojně, protože účinně chrání před funkci polymorfismus C++. Místo toho použijte virtuální funkce.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>CObject::IsSerializable  
 Ověřuje, zda tento objekt je vhodné pro serializaci.  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tento objekt lze serializovat; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pro třídu být serializovatelný, musí obsahovat jeho deklaraci [declare_serial –](run-time-object-model-services.md#declare_serial) musí obsahovat makro a implementaci [implement_serial –](run-time-object-model-services.md#implement_serial) makro.  
  
> [!NOTE]
>  Funkci není přepsat.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>Odstranění CObject::operator  
 Pro verzi knihovny operátor **odstranit** uvolní je paměť přidělená operátorem **nové**.  
  
```  
void PASCAL operator delete(void* p);

 
void PASCAL operator delete(
    void* p,
    void* pPlace);

 
void PASCAL operator delete(
    void* p,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>Poznámky  
 V ladicí verze operátor **odstranit** účastní příslušné schéma přidělení monitorování určený ke zjišťování nevracení paměti.  
  
 Pokud používáte řádek kódu  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 Před spuštěním vaší implementace v. CPP soubor, pak třetí verzi **odstranit** se použije, ukládání číslo a název souboru a řádku v přidělené bloku později vytváření sestav. Nemusíte si dělat starosti o poskytnutí další parametry; Makro o to postará za vás.  
  
 I když nepoužijete `DEBUG_NEW` v režimu ladění, zobrazí i zjištění paměti, ale bez generování sestav číslo řádku zdrojový soubor popsané výše.  
  
 Pokud přepíšete operátory **nové** a **odstranit**, ztrácí tato diagnostické funkce.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>CObject::operator nový  
 Pro verzi knihovny operátor **nové** provede přidělení paměti pro optimální v podobným způsobem `malloc`.  
  
```  
void* PASCAL operator new(size_t nSize);  
void* PASCAL operator new(size_t, void* p);

 
void* PASCAL operator new(
    size_t nSize,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>Poznámky  
 V ladicí verze operátor **nové** účastní příslušné schéma přidělení monitorování určený ke zjišťování nevracení paměti.  
  
 Pokud používáte řádek kódu  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 Před spuštěním vaší implementace v. CPP soubor, pak druhá verze **nové** se použije, ukládání číslo a název souboru a řádku v přidělené bloku později vytváření sestav. Nemusíte si dělat starosti o poskytnutí další parametry; Makro o to postará za vás.  
  
 I když nepoužijete `DEBUG_NEW` v režimu ladění, zobrazí i zjištění paměti, ale bez generování sestav číslo řádku zdrojový soubor popsané výše.  
  
> [!NOTE]
>  Pokud přepíšete tento operátor, je nutné také přepsat **odstranit**. Nepoužívejte standardní knihovna **_new_handler** funkce.  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>CObject::Serialize  
 Čtení nebo zápisu tento objekt z nebo do archivu.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 A `CArchive` objektu k serializaci do nebo z.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přepsat `Serialize` pro každou třídu, která chcete serializovat. Přepsané `Serialize` musí nejprve zavolat `Serialize` funkce základní třídy.  
  
 Musíte také použít [declare_serial –](run-time-object-model-services.md#declare_serial) makro ve vaší deklaraci třídy a musí používat [implement_serial –](run-time-object-model-services.md#implement_serial) makro k implementaci.  
  
 Použití [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) nebo [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) k určení, zda je archivu načítání nebo ukládání.  
  
 `Serialize`je volána metodou [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) a [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Tyto funkce jsou přidružené `CArchive` operátor vložení (  **< \<** ) a operátor extrakce (  **>>** ).  
  
 Serializace příklady najdete v článku [serializace: serializace objektu](../../mfc/serialization-serializing-an-object.md).  
  
### <a name="example"></a>Příklad  
 V tématu [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v všechny `CObject` příklady.  
  
 [!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



