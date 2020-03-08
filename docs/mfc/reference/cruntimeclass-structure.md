---
title: Struktura CRuntimeClass
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: 92979a10c18d9759e0ecc9f0785e56a97c0f0642
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874022"
---
# <a name="cruntimeclass-structure"></a>Struktura CRuntimeClass

Každá třída odvozená z `CObject` je asociována se strukturou `CRuntimeClass`, kterou lze použít k získání informací o objektu nebo jeho základní třídě za běhu.

## <a name="syntax"></a>Syntaxe

```
struct CRuntimeClass
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRuntimeClass:: CreateObject](#createobject)|Vytvoří objekt během běhu.|
|[CRuntimeClass:: from](#fromname)|Vytvoří objekt za běhu pomocí známého názvu třídy.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Určuje, zda je třída odvozena ze zadané třídy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CRuntimeClass:: m_lpszClassName](#m_lpszclassname)|Název třídy|
|[CRuntimeClass:: m_nObjectSize](#m_nobjectsize)|Velikost objektu v bajtech|
|[CRuntimeClass:: m_pBaseClass](#m_pbaseclass)|Ukazatel na `CRuntimeClass` strukturu základní třídy.|
|[CRuntimeClass:: m_pfnCreateObject](#m_pfncreateobject)|Ukazatel na funkci, která dynamicky vytvoří objekt.|
|[CRuntimeClass:: m_pfnGetBaseClass](#m_pfngetbaseclass)|Vrátí strukturu `CRuntimeClass` (k dispozici pouze v případě dynamicky propojených).|
|[CRuntimeClass:: m_wSchema](#m_wschema)|Číslo schématu třídy.|

## <a name="remarks"></a>Poznámky

`CRuntimeClass` je struktura, a proto nemá základní třídu.

Schopnost určit třídu objektu v době běhu je užitečná, když je potřeba provést kontrolu dalších typů argumentů funkce nebo když musíte napsat kód pro zvláštní účely na základě třídy objektu. Informace o třídě run-time nejsou přímo podporovány C++ jazykem.

`CRuntimeClass` poskytuje informace o souvisejícím C++ objektu, jako je například ukazatel na `CRuntimeClass` základní třídy a název třídy ASCII související třídy. Tato struktura také implementuje různé funkce, které lze použít k dynamickému vytváření objektů, určení typu objektu pomocí známého názvu a určení, zda je související Třída odvozena z konkrétní třídy.

Další informace o použití `CRuntimeClass`naleznete v článku [přístup k běhovým informacím o třídě](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CRuntimeClass`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="createobject"></a>CRuntimeClass:: CreateObject

Voláním této funkce dynamicky vytvoříte určenou třídu během běhu.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Známý název třídy, která se má vytvořit

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený objekt nebo hodnotu NULL, pokud název třídy nebyl nalezen nebo není dostatek paměti pro vytvoření objektu.

### <a name="remarks"></a>Poznámky

Třídy odvozené od `CObject` mohou podporovat dynamické vytváření, což je schopnost vytvořit v době běhu objekt zadané třídy. Třídy dokumentů, zobrazení a rámců by například měly podporovat dynamické vytváření. Další informace o dynamickém vytváření a `CreateObject` členu naleznete v tématu Třída [třídy CObject](../../mfc/using-cobject.md) a [Třída CObject: určení úrovní funkčnosti](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>CRuntimeClass:: from

Voláním této funkce načtete strukturu `CRuntimeClass` přidruženou k známému názvu.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Známý název třídy odvozené z `CObject`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CRuntimeClass`, který odpovídá názvu jako předaný v *lpszClassName*. Funkce vrátí hodnotu NULL, pokud nebyl nalezen žádný vyhovující název třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>CRuntimeClass::IsDerivedFrom

Voláním této funkce určíte, zda je volající Třída odvozena od třídy zadané v parametru *pBaseClass* .

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parametry

*pBaseClass*<br/>
Známý název třídy odvozené z `CObject`.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je třída, která volá `IsDerivedFrom`, odvozena ze základní třídy, jejíž `CRuntimeClass` struktura je uvedena jako parametr; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Vztah je určen pomocí "prochází" od třídy člena nahoru řetězu odvozených tříd od sebe až k hornímu. Tato funkce vrací hodnotu FALSE pouze v případě, že pro základní třídu nebyla nalezena shoda.

> [!NOTE]
>  Chcete-li použít strukturu `CRuntimeClass`, je nutné zahrnout makro IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE nebo IMPLEMENT_SERIAL v implementaci třídy, pro kterou chcete načíst informace o objektu modulu runtime.

Další informace o použití `CRuntimeClass`naleznete v článku [Třída CObject: přístup k běhovým informacím o třídě](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>CRuntimeClass:: m_lpszClassName

Řetězec zakončený hodnotou null obsahující název třídy ASCII.

### <a name="remarks"></a>Poznámky

Tento název lze použít k vytvoření instance třídy pomocí `FromName` členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>CRuntimeClass:: m_nObjectSize

Velikost objektu v bajtech.

### <a name="remarks"></a>Poznámky

Pokud má objekt datové členy, které odkazují na přidělenou paměť, nezahrnuje velikost této paměti.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>CRuntimeClass:: m_pBaseClass

Pokud vaše aplikace staticky odkazuje na knihovnu MFC, tento datový člen obsahuje ukazatel na `CRuntimeClass` strukturu základní třídy.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace dynamicky odkazuje na knihovnu MFC, přečtěte si téma [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>CRuntimeClass:: m_pfnCreateObject

Ukazatel funkce na výchozí konstruktor, který vytváří objekt třídy.

### <a name="remarks"></a>Poznámky

Tento ukazatel je platný pouze v případě, že třída podporuje dynamické vytváření; v opačném případě funkce vrátí hodnotu NULL.

##  <a name="m_pfngetbaseclass"></a>CRuntimeClass:: m_pfnGetBaseClass

Pokud vaše aplikace používá knihovnu MFC jako sdílenou knihovnu DLL, tento datový člen odkazuje na funkci, která vrací `CRuntimeClass` strukturu základní třídy.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace staticky odkazuje na knihovnu MFC, přečtěte si téma [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>CRuntimeClass:: m_wSchema

Číslo schématu (-1 pro neserializovatelné třídy).

### <a name="remarks"></a>Poznámky

Další informace o číslech schématu naleznete v tématu [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makro.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject:: GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
