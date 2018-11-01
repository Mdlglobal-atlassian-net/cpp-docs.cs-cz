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
ms.openlocfilehash: 54f47fd931374df0e9f71c0d946845d8d5b16695
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452699"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass – struktura

Každá třída odvozena z `CObject` je přidružena `CRuntimeClass` struktura, která vám pomůže získat informace o objektu nebo její základní třídě v době běhu.

## <a name="syntax"></a>Syntaxe

```
struct CRuntimeClass
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Vytvoří objekt za běhu.|
|[CRuntimeClass::FromName](#fromname)|Vytvoří objekt za běhu pomocí názvu třídy zkušenosti.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Určuje, pokud je třída odvozena z dané třídy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Název třídy.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Velikost objektu v bajtech.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Ukazatel `CRuntimeClass` struktura základní třídy.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Ukazatel na funkci, která dynamicky vytvoří objekt.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Vrátí `CRuntimeClass` struktury (pouze k dispozici, pokud dynamicky propojené).|
|[CRuntimeClass::m_wSchema](#m_wschema)|Číslo schéma třídy.|

## <a name="remarks"></a>Poznámky

`CRuntimeClass` je struktura a proto nemá základní třídu.

Schopnost určit třídu objektu v době běhu je užitečné, když je potřeba další kontrolu argumentů funkce typu, nebo když je nutné napsat kód zvláštní účely na základě třídy objektu. Informace o třídě za běhu se nepodporuje přímo v jazyce C++.

`CRuntimeClass` poskytuje informace o souvisejících objekt jazyka C++, jako je ukazatel `CRuntimeClass` základní třídu a název třídy ASCII související třídy. Tato struktura implementuje také různé funkce, které je možné dynamicky vytvořit objekty pomocí názvu známé a určení, pokud je související třída odvozena z určité třídy určující typ objektu.

Další informace o používání `CRuntimeClass`, najdete v článku [přístup k informacím o třídě Run-Time](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CRuntimeClass`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="createobject"></a>  CRuntimeClass::CreateObject

Voláním této funkce dynamicky za běhu se vytvářejí dané třídy.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Známé název třídy, který se má vytvořit.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený objekt nebo hodnota NULL, pokud název třídy nebyl nalezen nebo není dostatek paměti k vytvoření objektu.

### <a name="remarks"></a>Poznámky

Třídy odvozené z `CObject` může podporovat dynamické vytváření, což je schopnost vytvářet objekt z dané třídy v době běhu. Dokumentu, zobrazení a rámečku třídy, například by měla podporovat dynamické vytváření. Další informace o dynamické vytváření a `CreateObject` člen, naleznete v tématu [CObject – třída](../../mfc/using-cobject.md) a [CObject – třída: určení úrovní funkčnosti](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>  CRuntimeClass::FromName

Voláním této funkce načtete `CRuntimeClass` struktura přidružené k názvu zkušenosti.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parametry

*lpszClassName*<br/>
Známé název třídy odvozené z `CObject`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CRuntimeClass` objektu odpovídající názvu jako úspěšný v *lpszClassName*. Funkce vrátí hodnotu NULL, pokud nebyl nalezen žádný odpovídající název třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom

Voláním této funkce k určení, pokud je volání třída odvozena z třídy určené v *pBaseClass* parametru.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

```

### <a name="parameters"></a>Parametry

*pBaseClass*<br/>
Známé název třídy odvozené z `CObject`.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud volání metody třídy `IsDerivedFrom` odvozené ze základní třídy, jejichž `CRuntimeClass` struktura je daný jako parametr; jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Určuje vztah "walking" ze člena třídy řetězem odvozených tříd až po horní části. Tato funkce pouze vrátí hodnotu FALSE, pokud není nalezena žádná shoda pro základní třídu.

> [!NOTE]
>  Použít `CRuntimeClass` struktury, musí obsahovat IMPLEMENT_DYNAMIC IMPLEMENT_DYNCREATE a IMPLEMENT_SERIAL – makro v implementaci třídy, pro který chcete načíst informace o objektu za běhu.

Další informace o používání `CRuntimeClass`, najdete v článku [CObject – třída: přístup k informacím o třídě Run-Time](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName

Řetězec zakončený hodnotou null obsahující název třídy ASCII.

### <a name="remarks"></a>Poznámky

Tento název slouží k vytvoření instance třídy pomocí `FromName` členskou funkci.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize

Velikost objektu v bajtech.

### <a name="remarks"></a>Poznámky

Pokud objekt má datové členy, které odkazují na přidělené paměti, velikost paměti, že není zahrnuté.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass

Pokud vaše aplikace staticky propojuje ke knihovně MFC, tomuto datovému členu obsahuje ukazatel `CRuntimeClass` struktura základní třídy.

### <a name="remarks"></a>Poznámky

Pokud aplikace dynamicky propojuje ke knihovně MFC, přečtěte si téma [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject

Ukazatele na funkci na výchozí konstruktor, který vytvoří objekt třídy.

### <a name="remarks"></a>Poznámky

Tento ukazatel je platná pouze pokud třída podporuje dynamické vytváření; v opačném případě vrátí hodnotu NULL.

##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass

Pokud vaše aplikace používá knihovnu MFC jako sdílenou knihovnu DLL, tomuto datovému členu odkazuje na funkci, která vrátí `CRuntimeClass` struktura základní třídy.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace staticky propojuje ke knihovně MFC, přečtěte si téma [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema

Schéma číslo (-1 pro nonserializable třídy).

### <a name="remarks"></a>Poznámky

Další informace o schématu čísla, najdete v článku [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) – makro.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)

