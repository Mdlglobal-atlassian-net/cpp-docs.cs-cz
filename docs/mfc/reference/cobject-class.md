---
title: CObject – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: 515c4e90ee6ab77a6c7c1ae108393ea1aafb7c17
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855270"
---
# <a name="cobject-class"></a>CObject – třída

Základní třída zabezpečení pro knihovna Microsoft Foundation Class.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObject:: CObject](#cobject)|Výchozí konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObject:: AssertValid](#assertvalid)|Ověří integritu tohoto objektu.|
|[CObject::D UMP](#dump)|Vytvoří diagnostický výpis tohoto objektu.|
|[CObject:: GetRuntimeClass](#getruntimeclass)|Vrací strukturu `CRuntimeClass` odpovídající třídě tohoto objektu.|
|[CObject:: IsKindOf](#iskindof)|Testuje vztah tohoto objektu na danou třídu.|
|[CObject:: deserializovatelné](#isserializable)|Testuje, zda lze tento objekt serializovat.|
|[CObject:: serializovat](#serialize)|Načte nebo uloží objekt z/do archivu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CObject:: operator delete](#operator_delete)|Speciální operátor **Delete**|
|[CObject:: operator new](#operator_new)|Speciální operátor **New**|

## <a name="remarks"></a>Poznámky

Slouží jako kořenový adresář nejen pro třídy knihovny, například `CFile` a `CObList`, ale také pro třídy, které zapisujete. `CObject` poskytuje základní služby, včetně

- Podpora serializace

- Běhové informace třídy

- Výstup diagnostiky objektů

- Kompatibilita s třídami kolekcí

Všimněte si, že `CObject` nepodporuje vícenásobnou dědičnost. Vaše odvozené třídy mohou mít pouze jednu `CObject` základní třídu a `CObject` musí být v hierarchii v hierarchii. Je však povoleno, aby měly struktury a třídy odvozené od `CObject`v prostředí s vícenásobnou dědičností na pravé straně.

Pokud použijete některá z volitelných maker v implementaci a deklaracích třídy, budete mít velké výhody z `CObject` odvození.

Makra první úrovně, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) a [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), umožňují přístup k názvu třídy a její pozici v hierarchii v době běhu. To zase umožňuje smysluplný diagnostický dumping.

Makra druhé úrovně, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), obsahují všechny funkce maker první úrovně a umožňují, aby objekt byl "serializován" do a z "archivu".

Informace o tom, jak obecně odvozovat třídy C++ a třídy Microsoft Foundation a pomocí `CObject`, naleznete v tématu [using CObject](../../mfc/using-cobject.md) and [Serialization](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="assertvalid"></a>CObject:: AssertValid

Ověří integritu tohoto objektu.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

`AssertValid` provádí kontrolu platnosti tohoto objektu kontrolou jeho vnitřního stavu. V ladicí verzi knihovny `AssertValid` možné vyhodnotit, takže program ukončí zprávu se zprávou, která obsahuje číslo řádku a název souboru, kde se kontrolní výraz nezdařil.

Při psaní vlastní třídy byste měli přepsat funkci `AssertValid`, aby poskytovala diagnostické služby pro sebe a jiné uživatele vaší třídy. Přepsaná `AssertValid` obvykle zavolá funkci `AssertValid` své základní třídy před kontrolou datových členů, které jsou jedinečné pro odvozenou třídu.

Vzhledem k tomu, že `AssertValid` je funkce **const** , nebudete mít oprávnění měnit stav objektu během testu. Vaše vlastní odvozené třídy `AssertValid` Functions by neměly vyvolat výjimky, ale spíše by měly uplatnit, zda zjišťují neplatná data objektů.

Definice "platnosti" závisí na třídě objektu. Jako pravidlo by funkce měla provést "omezené kontroly". To znamená, že pokud objekt obsahuje ukazatele na jiné objekty, měla by se zobrazit, zda ukazatelé nejsou null, ale by neměl provádět testování platnosti objektů, na které odkazují ukazatele.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Další příklad naleznete v tématu [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

##  <a name="cobject"></a>CObject:: CObject

Tyto funkce jsou standardní `CObject` konstruktory.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parametry

*objectSrc*<br/>
Odkaz na jiný `CObject`

### <a name="remarks"></a>Poznámky

Výchozí verze je automaticky volána konstruktorem odvozené třídy.

Pokud je vaše třída serializovatelný (zahrnuje makro IMPLEMENT_SERIAL), pak musíte mít výchozí konstruktor (konstruktor bez argumentů) ve vaší deklaraci třídy. Pokud nepotřebujete výchozí konstruktor, deklarujte privátní nebo chráněný konstruktor "Empty". Další informace najdete v tématu [použití CObject](../../mfc/using-cobject.md).

Standardní C++ konstruktor pro kopírování tříd provádí kopírování členů do členů. Přítomnost soukromého konstruktoru `CObject` Copy garantuje chybovou zprávu kompilátoru, pokud je konstruktor Copy třídy požadován, ale není k dispozici. Proto je nutné poskytnout kopírovací konstruktor, pokud vaše třída vyžaduje tuto možnost.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané v příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>CObject::D UMP

Vypíše obsah objektu do objektu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) .

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parametry

*DC*<br/>
Kontext výpisu diagnostiky pro dumping, obvykle `afxDump`.

### <a name="remarks"></a>Poznámky

Při psaní vlastní třídy byste měli přepsat funkci `Dump`, aby poskytovala diagnostické služby pro sebe a jiné uživatele vaší třídy. Přepsaná `Dump` obvykle zavolá funkci `Dump` své základní třídy před tiskem datových členů, které jsou jedinečné pro odvozenou třídu. `CObject::Dump` vytiskne název třídy, pokud vaše třída používá makro `IMPLEMENT_DYNAMIC` nebo IMPLEMENT_SERIAL.

> [!NOTE]
>  Funkce `Dump` by neměla tisknout znak nového řádku na konci jeho výstupu.

`Dump` volání vyvolají pouze v ladicí verzi knihovna Microsoft Foundation Class. Volání v závorkách, deklarace funkcí a implementace funkcí s **#ifdef _DEBUG**/ `#endif` příkazy pro podmíněnou kompilaci.

Vzhledem k tomu, že `Dump` je funkce **const** , nemůžete změnit stav objektu během výpisu.

[Operátor vložení CDumpContext (< <)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) volá `Dump` při vložení `CObject`ho ukazatele.

`Dump` povoluje pouze "acyklického" dumping objektů. Můžete například vypsat seznam objektů, ale pokud jeden z objektů je samotný seznam, nakonec přetečení zásobníku.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>CObject:: GetRuntimeClass

Vrací strukturu `CRuntimeClass` odpovídající třídě tohoto objektu.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) odpovídající třídě tohoto objektu; nikdy **null**.

### <a name="remarks"></a>Poznámky

Pro každou třídu odvozenou od `CObject`existuje jedna struktura `CRuntimeClass`. Členy struktury jsou následující:

- **LPCSTR m_lpszClassName** Řetězec zakončený hodnotou null obsahující název třídy ASCII.

- **int m_nObjectSize** Velikost objektu v bajtech. Pokud má objekt datové členy, které odkazují na přidělenou paměť, nezahrnuje velikost této paměti.

- **M_wSchema uint** Číslo schématu (-1 pro neserializovatelné třídy). Popis čísla schématu naleznete v makru [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

- **CObject\* (PASCAL\* m_pfnCreateObject) ()** Ukazatel funkce na výchozí konstruktor, který vytváří objekt třídy (platný pouze v případě, že třída podporuje dynamické vytváření; v opačném případě vrátí **hodnotu null**).

- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** Pokud je vaše aplikace dynamicky propojena s verzí AFXDLL – knihovny MFC, ukazatel na funkci, která vrací `CRuntimeClass` strukturu základní třídy.

- **CRuntimeClass\* m_pBaseClass** Pokud je vaše aplikace staticky propojena s knihovnou MFC, ukazatel na `CRuntimeClass` strukturu základní třídy.

Tato funkce vyžaduje použití makra [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)nebo [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) v implementaci třídy. V opačném případě se zobrazí nesprávné výsledky.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>CObject:: IsKindOf

Testuje vztah tohoto objektu na danou třídu.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) spojenou s vaší třídou odvozenou od `CObject`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt odpovídá třídě; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce testuje *pClass* a zjistí, zda (1) je objekt zadané třídy nebo (2) je objekt třídy odvozené ze zadané třídy. Tato funkce funguje pouze pro třídy deklarované pomocí makra [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)nebo [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

Nepoužívejte tuto funkci rozsáhle, protože se C++ tím přepírá funkce polymorfismus. Místo toho použijte virtuální funkce.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>CObject:: deserializovatelné

Testuje, zda má tento objekt nárok na serializaci.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je možné tento objekt serializovat; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pro třídu, která má být serializovatelný, musí její deklarace obsahovat [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makro a implementace musí obsahovat makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

> [!NOTE]
>  Nepřepisujte tuto funkci.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>CObject:: operator delete

Pro vydanou verzi knihovny, operátor **Delete** uvolní paměť přidělenou operátorem **New**.

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

V ladicí verzi se operátor **Delete** účastní schématu pro monitorování přidělování, které je určené k detekci nevracení paměti.

Použijete-li řádek kódu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

před kteroukoli z vašich implementací v. CPP, pak se použije třetí verze **Delete** , která uloží název souboru a číslo řádku do přiděleného bloku pro pozdější vytváření sestav. Nemusíte se starat o poskytnutí dalších parametrů; makro se za vás zajímá.

I v případě, že DEBUG_NEW v režimu ladění nepoužíváte, stále se vám vrátí detekce nevracení, ale bez ohledu na číslo řádku zdrojového souboru, který je popsaný výše.

Pokud přepíšete operátory **New** a **Delete**, propadne tuto diagnostickou funkci.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané v příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>CObject:: operator new

Pro vydanou verzi knihovny, operátor **New** provede optimální přidělení paměti způsobem podobným `malloc`.

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Poznámky

V ladicí verzi se **Nový** operátor účastní schématu pro monitorování přidělování, které je určené k detekci nevracení paměti.

Použijete-li řádek kódu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

před kteroukoli z vašich implementací v. CPP, pak se použije druhá verze **nového** , která uloží název souboru a číslo řádku do přiděleného bloku pro pozdější vytváření sestav. Nemusíte se starat o poskytnutí dalších parametrů; makro se za vás zajímá.

I v případě, že DEBUG_NEW v režimu ladění nepoužíváte, stále se vám vrátí detekce nevracení, ale bez ohledu na číslo řádku zdrojového souboru, který je popsaný výše.

> [!NOTE]
>  Pokud přepíšete Tento operátor, je nutné také přepsat příkaz **Delete**. Nepoužívejte funkci standardní knihovny `_new_handler`.

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané v příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>CObject:: serializovat

Přečte nebo zapisuje tento objekt z nebo do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*snížen*<br/>
Objekt `CArchive` k serializaci do nebo z.

### <a name="remarks"></a>Poznámky

Je nutné přepsat `Serialize` pro každou třídu, kterou chcete serializovat. Přepsaná `Serialize` musí nejprve volat funkci `Serialize` své základní třídy.

Je také nutné použít makro [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) v deklaraci třídy a je nutné použít makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) v implementaci.

Použijte [CArchive:: IsLoaded](../../mfc/reference/carchive-class.md#isloading) nebo [CArchive:: Uložit](../../mfc/reference/carchive-class.md#isstoring) k určení, zda se archiv načítá nebo ukládá.

`Serialize` je volána pomocí [CArchive:: ReadObject](../../mfc/reference/carchive-class.md#readobject) a [CArchive:: WriteObject](../../mfc/reference/carchive-class.md#writeobject). Tyto funkce jsou spojeny s operátorem vkládání `CArchive` ( **<\<** ) a operátorem pro extrakci ( **>>** ).

Příklady serializace naleznete v článku [serializace: serializace objektu](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Příklad

Seznam `CAge` třídy používané ve všech příkladech `CObject` naleznete v tématu [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) .

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
