---
title: CRuntimeClass – struktura
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: a58b9c97d5683423a0f81f6b5424f19f987943bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318554"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass – struktura

Každá třída odvozená z `CObject` `CRuntimeClass` je přidružena ke struktuře, kterou můžete použít k získání informací o objektu nebo jeho základní třídě za běhu.

## <a name="syntax"></a>Syntaxe

```
struct CRuntimeClass
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Vytvoří objekt za běhu.|
|[CRuntimeClass::FromName](#fromname)|Vytvoří objekt za běhu pomocí známého názvu třídy.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Určuje, zda je třída odvozena od zadané třídy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Název třídy|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Velikost objektu v bajtů.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Ukazatel na `CRuntimeClass` strukturu základní třídy.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Ukazatel na funkci, která dynamicky vytváří objekt.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Vrátí `CRuntimeClass` strukturu (k dispozici pouze při dynamice propojené).|
|[CRuntimeClass::m_wSchema](#m_wschema)|Číslo schématu třídy.|

## <a name="remarks"></a>Poznámky

`CRuntimeClass`je struktura, a proto nemá základní třídu.

Schopnost určit třídu objektu za běhu je užitečná, když je potřeba další typ kontroly argumentů funkce nebo když je nutné napsat speciální kód založený na třídě objektu. Informace o třídě za běhu nejsou podporovány přímo jazykem Jazyka C++.

`CRuntimeClass`obsahuje informace o související objekt C++, jako `CRuntimeClass` je například ukazatel na základní třídy a název třídy ASCII související třídy. Tato struktura také implementuje různé funkce, které lze dynamicky vytvářet objekty, určení typu objektu pomocí známého názvu a určení, zda je související třída odvozena z určité třídy.

Další informace o `CRuntimeClass`použití naleznete v článku [Přístup k informacím o třídě za běhu](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CRuntimeClass`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a>CRuntimeClass::CreateObject

Volání této funkce dynamicky vytvořit zadanou třídu za běhu.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*název lpszClassName*<br/>
Známý název třídy, která má být vytvořena.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený objekt nebo NULL, pokud není nalezen název třídy nebo není dostatek paměti k vytvoření objektu.

### <a name="remarks"></a>Poznámky

Třídy odvozené z `CObject` může podporovat dynamické vytváření, což je schopnost vytvořit objekt zadané třídy za běhu. Například třídy dokumentu, zobrazení a rámce by měly podporovat dynamické vytváření. Další informace o dynamickém `CreateObject` vytváření a členu naleznete v tématu [CObject Class](../../mfc/using-cobject.md) a [CObject Class: Specifying Levels of Functionality](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Příklad

  Viz příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassfromname"></a><a name="fromname"></a>CRuntimeClass::FromName

Volání této funkce `CRuntimeClass` načíst strukturu přidruženou ke známému názvu.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*název lpszClassName*<br/>
Známý název třídy odvozené `CObject`z .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CRuntimeClass` objekt, odpovídající názvu jako předané v *lpszClassName*. Funkce vrátí hodnotu NULL, pokud nebyl nalezen žádný odpovídající název třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a>CRuntimeClass::IsDerivedFrom

Volání této funkce k určení, pokud volající třída je odvozena z třídy zadané v *parametru pBaseClass.*

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parametry

*pBaseClass*<br/>
Známý název třídy odvozené `CObject`z .

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud volání `IsDerivedFrom` třídy je odvozen `CRuntimeClass` od základní třídy, jejíž struktura je uveden jako parametr; jinak FALSE.

### <a name="remarks"></a>Poznámky

Vztah je určen "chůze" z členské třídy do řetězce odvozených tříd až na vrchol. Tato funkce vrátí hodnotu NEPRAVDA pouze v případě, že pro základní třídu není nalezena žádná shoda.

> [!NOTE]
> Chcete-li `CRuntimeClass` použít strukturu, musíte zahrnout IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE nebo IMPLEMENT_SERIAL makro v implementaci třídy, pro kterou chcete načíst informace o objektu za běhu.

Další informace o `CRuntimeClass`použití naleznete v článku [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a>CRuntimeClass::m_lpszClassName

Řetězec s nulovým ukončeným hodnotou obsahující název třídy ASCII.

### <a name="remarks"></a>Poznámky

Tento název lze použít k vytvoření instance `FromName` třídy pomocí členské funkce.

### <a name="example"></a>Příklad

  Viz příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a>CRuntimeClass::m_nObjectSize

Velikost objektu v bajtů.

### <a name="remarks"></a>Poznámky

Pokud objekt má datové členy, které odkazují na přidělené paměti, velikost této paměti není zahrnuta.

### <a name="example"></a>Příklad

  Viz příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a>CRuntimeClass::m_pBaseClass

Pokud vaše aplikace staticky odkazy na knihovnu MFC, tento datový člen obsahuje ukazatel na `CRuntimeClass` strukturu základní třídy.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace dynamicky odkazuje na knihovnu knihovny MFC, [přečtěte si m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Příklad

  Viz příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a>CRuntimeClass::m_pfnCreateObject

Ukazatel funkce na výchozí konstruktor, který vytvoří objekt vaší třídy.

### <a name="remarks"></a>Poznámky

Tento ukazatel je platný pouze v případě, že třída podporuje dynamické vytváření; v opačném případě vrátí funkce hodnotu NULL.

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a>CRuntimeClass::m_pfnGetBaseClass

Pokud vaše aplikace používá knihovnu knihovny MFC jako sdílenou knihovnu `CRuntimeClass` DLL, tento datový člen odkazuje na funkci, která vrací strukturu základní třídy.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace staticky odkazuje na knihovnu knihovny MFC, [přečtěte si m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Příklad

  Viz příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a>CRuntimeClass::m_wSchema

Číslo schématu ( -1 pro neserializovatelné třídy).

### <a name="remarks"></a>Poznámky

Další informace o číslech schémat naleznete v [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makra.

### <a name="example"></a>Příklad

  Viz příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObjekt::IskindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
