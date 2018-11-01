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
ms.openlocfilehash: eb0580f6fef39df29d66e15cfd051a0460cb8d56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584012"
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
|[CObject::AssertValid](#assertvalid)|Ověří integritu tento objekt.|
|[CObject::Dump](#dump)|Vytvoří diagnostiky s výpisem paměti tohoto objektu.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Vrátí `CRuntimeClass` struktury odpovídající tento objekt třídy.|
|[CObject::IsKindOf](#iskindof)|Testuje vztah tohoto objektu do dané třídy.|
|[CObject::IsSerializable](#isserializable)|Otestuje, zda tento objekt lze serializovat.|
|[CObject::Serialize](#serialize)|Načte nebo uloží objekt z/do archivu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CObject::operator delete](#operator_delete)|Speciální **odstranit** operátor.|
|[CObject::operator nové](#operator_new)|Speciální **nové** operátor.|

## <a name="remarks"></a>Poznámky

Slouží jako kořenový nejen pro knihovny tříd jako `CFile` a `CObList`, ale také pro třídy, které napíšete. `CObject` poskytuje základní služby, včetně

- Podpora serializace

- Informace o třídě za běhu

- Diagnostický výstup objektu

- Kompatibilita s třídy kolekce

Všimněte si, že `CObject` nepodporuje vícenásobnou dědičnost. Odvozené třídy může mít pouze jeden `CObject` základní třídu a že `CObject` musí být úplně vlevo v hierarchii. Je přípustné, ale mít struktury a bez- `CObject`-odvozené třídy v pravém větví vícenásobné dědičnosti.

Hlavní výhody značným `CObject` odvození, pokud použijete některé volitelné maker v implementaci třídy a deklarace.

Makra první úrovně [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) a [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), povolení přístupu za běhu k názvu třídy a jeho umístění v hierarchii. To, zase umožňuje smysluplné diagnostické výpis.

Makra druhé úrovně [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), zahrnují všechny funkce, které jsou součástí makra první úrovně a umožňují objektu "serializovat" do a z "archiv."

Informace o používání a odvozené třídy C++ a tříd Microsoft Foundation classes obecně `CObject`, naleznete v tématu [použití objektů CObject](../../mfc/using-cobject.md) a [serializace](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="assertvalid"></a>  CObject::AssertValid

Ověří integritu tento objekt.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Poznámky

`AssertValid` provede kontrolu platnosti u tohoto objektu tak, že zkontrolujete jeho vnitřního stavu. V ladicí verzi knihovny `AssertValid` může kontrolní výraz a ukončete program a zobrazí se zpráva, která obsahuje číslo řádku a název souboru, kde kontrolní výraz je neplatný.

Při psaní vlastní třídu, kterou byste měli přepsat `AssertValid` funkce poskytují diagnostické služby pro vás i ostatní uživatelé z vaší třídy. Přepsané `AssertValid` obvykle volá `AssertValid` funkce své základní třídy před vrácením datové členy, které jsou jedinečné pro odvozenou třídu.

Protože `AssertValid` je **const** funkce nejsou povoleny změny stavu objektu během testu. Odvozené třídy `AssertValid` funkce by neměla vyvolávat výjimky, ale místo toho by měl vyhodnocení, jestli zjistí neplatný objekt data.

Definice "platnosti" závisí na třídě objektu. Zpravidla funkce by měla kontrola "bez podstruktury." To znamená pokud objekt obsahuje odkazy na jiné objekty, ji by měl zkontrolujte, zda že ukazatele nemají hodnotu null, ale to neměli provádět platnosti testování na objekty, na které odkazuje ukazatele.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Další příklad naleznete v tématu [afxdoforallobjects –](diagnostic-services.md#afxdoforallobjects).

##  <a name="cobject"></a>  CObject::CObject

Tyto funkce jsou standardní `CObject` konstruktory.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parametry

*objectSrc*<br/>
Odkaz na jiný `CObject`

### <a name="remarks"></a>Poznámky

Výchozí verze je automaticky volána konstruktoru odvozené třídy.

Pokud je vaše třída serializovatelný (to zahrnuje IMPLEMENT_SERIAL – makro), pak musí mít výchozí konstruktor (konstruktor bez argumentů) v deklaraci vaší třídy. Pokud nepotřebujete výchozí konstruktor, deklarovat soukromé nebo chráněné "prázdný" konstruktor. Další informace najdete v tématu [použití objektů CObject](../../mfc/using-cobject.md).

Kopie konstruktoru pro standardní C++ výchozí třída nemá kopii člena člena. Přítomnost privátní `CObject` kopírovací konstuktor zaručuje chybových zpráv kompilátoru, pokud konstruktor kopie třídy je potřeba, ale není k dispozici. Proto je nutné zadat kopírovací konstruktor, pokud tato možnost vyžaduje třídu.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>  CObject::Dump

Vypíše obsah váš objekt mohl [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objektu.

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parametry

*řadič domény*<br/>
Kontext diagnostiky s výpisem paměti pro výpis obvykle `afxDump`.

### <a name="remarks"></a>Poznámky

Při psaní vlastní třídu, kterou byste měli přepsat `Dump` funkce poskytují diagnostické služby pro vás i ostatní uživatelé z vaší třídy. Přepsané `Dump` obvykle volá `Dump` funkce své základní třídy před tiskem datové členy, které jsou jedinečné pro odvozenou třídu. `CObject::Dump` Vytiskne název třídy, pokud používá třídu `IMPLEMENT_DYNAMIC` nebo IMPLEMENT_SERIAL – makro.

> [!NOTE]
>  Vaše `Dump` funkce by neměl tisk znakem na konci jeho výstup.

`Dump` volání smysl pouze v ladicí verzi knihovny Microsoft Foundation Class. By měl párování volání, deklarace funkcí a implementací funkce s **#ifdef _DEBUG** /  `#endif` příkazy podmíněné kompilace.

Protože `Dump` je **const** funkce nejsou povoleny změny stavu objektů při výpisu paměti.

[CDumpContext vložení (<<) – operátor](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) volání `Dump` při `CObject` ukazatel je vložen.

`Dump` povoluje pouze "Acyklické" výpis objektů. Je možné vypsat seznam objektů, například, ale pokud jeden z objektů je samotný seznam, bude nakonec přetečení zásobníku.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass

Vrátí `CRuntimeClass` struktury odpovídající tento objekt třídy.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktuře odpovídající tento objekt třídy; nikdy **NULL**.

### <a name="remarks"></a>Poznámky

Existuje jedna `CRuntimeClass` strukturu pro každý `CObject`-odvozené třídy. Členy struktury jsou následující:

- **LPCSTR m_lpszClassName** řetězec zakončený hodnotou null obsahující název třídy ASCII.

- **int m_nObjectSize** velikost objektu v bajtech. Pokud objekt má datové členy, které odkazují na přidělené paměti, velikost paměti, že není zahrnuté.

- **UINT m_wSchema** číslo schématu (-1 pro nonserializable třídy). Zobrazit [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) – makro popis číslo schématu.

- **CObject –\* (PASCAL\* m_pfnCreateObject) ()** ukazatele na funkci na výchozí konstruktor, který vytvoří objekt třídy (platné pouze v případě, že třída podporuje dynamické vytváření; v opačném případě vrátí **NULL** ).

- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** Pokud vaše aplikace je dynamicky propojena s AFXDLL – verze knihovny MFC, ukazatel na funkci vracející `CRuntimeClass` struktura základní třídy.

- **CRuntimeClass\* m_pBaseClass** Pokud vaše aplikace staticky propojené do MFC, ukazatel `CRuntimeClass` struktura základní třídy.

Tato funkce vyžaduje použití [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), nebo [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) – makro v implementaci třídy. V opačném případě získáte nesprávné výsledky.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>  CObject::IsKindOf

Testuje vztah tohoto objektu do dané třídy.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Ukazatel na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura přidružené k vaší `CObject`-odvozené třídy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt odpovídá třídy; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce testuje *pClass* zda (1) je objekt z dané třídy nebo (2) je objekt třídy odvozené z dané třídy. Tato funkce funguje pouze pro třídy deklarované s [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate), nebo [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) – makro.

Nepoužívejte tuto funkci výrazně, protože to anuluje polymorfismus funkcí jazyka C++. Místo toho použijte virtuální funkce.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>  CObject::IsSerializable

Ověřuje, zda tento objekt je vhodné pro serializaci.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tento objekt lze serializovat; jinak 0.

### <a name="remarks"></a>Poznámky

Pro třídu jako serializovatelný, musí obsahovat deklaraci [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) musí obsahovat makra a implementaci [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) – makro.

> [!NOTE]
>  Tuto funkci nelze přepsat.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>  CObject::operator delete

Pro verzi knihovny operátor **odstranit** uvolní paměť přidělenou operátorem **nové**.

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

V ladicí verzi operátoru **odstranit** podílí na režimu přidělování monitorování navržené k detekování nevracení paměti.

Pokud použijete řádek kódu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

Před spuštěním vaší implementace v. CPP souborů pak třetí verzi **odstranit** se použije, ukládání do přiděleného bloku později vytváření sestav název souboru a číslo řádku. Není nutné se starat o poskytnutí nadbytečné parametry; Makro o to postará za vás.

I když nepoužijete DEBUG_NEW v režimu ladění, zobrazí i detekci nevrácení paměti, ale bez generování sestav číslo řádku zdrojového souboru je popsáno výše.

Pokud přepíšete operátory **nové** a **odstranit**, dvouletého období tato diagnostické funkce.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>  CObject::operator nové

Pro verzi knihovny operátor **nové** vede přidělení paměti pro optimální podobným způsobem `malloc`.

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Poznámky

V ladicí verzi operátoru **nové** podílí na režimu přidělování monitorování navržené k detekování nevracení paměti.

Pokud použijete řádek kódu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

Před spuštěním vaší implementace v. CPP souborů pak druhou verzi **nové** se použije, ukládání do přiděleného bloku později vytváření sestav název souboru a číslo řádku. Není nutné se starat o poskytnutí nadbytečné parametry; Makro o to postará za vás.

I když nepoužijete DEBUG_NEW v režimu ladění, zobrazí i detekci nevrácení paměti, ale bez generování sestav číslo řádku zdrojového souboru je popsáno výše.

> [!NOTE]
>  Pokud přepíšete tento operátor, musí také přepsat **odstranit**. Nepoužívejte standardní knihovně `_new_handler` funkce.

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` třída používaná v `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>  CObject::Serialize

Čtení nebo zápis tento objekt z nebo do archivu.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
A `CArchive` objektu určeného k serializaci nebo odchozí.

### <a name="remarks"></a>Poznámky

Je nutné přepsat `Serialize` pro každou třídu, kterou chcete serializovat. Přepsané `Serialize` musí nejprve zavolat `Serialize` funkce své základní třídy.

Musíte taky použít [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) – makro v deklaraci vaší třídy a je nutné použít [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) – makro v implementaci.

Použití [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) nebo [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) k určení, zda je načítání nebo ukládání archivu.

`Serialize` je volán [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) a [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Tyto funkce jsou spojené s `CArchive` operátor vkládání ( **< \<**) a extrakce – operátor ( **>>**).

Příklady serializace naleznete v článku [serializace: serializace objektu](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Příklad

Zobrazit [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) seznam `CAge` Třída použitá ve všech `CObject` příklady.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)

