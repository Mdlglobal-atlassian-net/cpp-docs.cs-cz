---
title: Makra registru
ms.date: 08/19/2019
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: fd012b4300f4cd72cdc9ab363b770ac1dbefa06e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326047"
---
# <a name="registry-macros"></a>Makra registru

Tato makra definují užitečná knihovna typů a zařízení registru.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Označuje, že chcete, aby registrační kód objektu byl v objektu, aby se zabránilo závislosti na knihovně ATL. Knihovny dll.|
|[DECLARE_LIBID](#declare_libid)|Poskytuje způsob, jak knihovna ATL získat *libid* knihovny typů.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Zabraňuje výchozí registraci atl.|
|[DECLARE_REGISTRY](#declare_registry)|Zadá nebo odebere položku hlavního objektu v systémovém registru.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Určuje informace potřebné k automatické *registraci appid*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Vyhledá pojmenovaný prostředek a spustí v něm skript registru.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Vyhledá prostředek identifikovaný číslem ID a spustí v něm skript registru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Symbol, který označuje, že chcete registrační kód objektu být v objektu, aby se zabránilo závislosti na knihovně ATL. Knihovny dll.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Poznámky

Při definování ATL_STATIC_REGISTRY byste měli použít následující kód:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a>DECLARE_LIBID

Poskytuje způsob, jak knihovna ATL získat *libid* knihovny typů.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parametry

*libid*<br/>
Identifikátor GUID knihovny typů.

### <a name="remarks"></a>Poznámky

Použijte DECLARE_LIBID `CAtlModuleT`v odvozené třídě.

### <a name="example"></a>Příklad

Nepřiřazené projekty knihovny ATL generované průvodcem budou mít vzorek použití tohoto makra.

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Pokud se chcete vyhnout výchozí registraci atl pro třídu, ve které se toto makro zobrazí, použijte DECLARE_NO_REGISTRY.

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a>DECLARE_REGISTRY

Zadá registraci standardní třídy do systémového registru nebo ji odebere ze systémového registru.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>Parametry

*třída*<br/>
[v] Součástí je zpětná kompatibilita.

*Pid*<br/>
[v] LPCTSTR, který je identifikátor programu specifické pro verzi.

*vpid*<br/>
[v] LPCTSTR, který je identifikátor programu nezávislý na verzi.

*Nid*<br/>
[v] UINT, který je index řetězce prostředků v registru použít jako popis programu.

*příznaky*<br/>
[v] DWORD obsahující model zřetězení programu v registru. Musí být jedna z následujících hodnot: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.

### <a name="remarks"></a>Poznámky

Standardní registrace se skládá z CLSID, ID programu, ID programu nezávislého na verzi, řetězce popisu a modelu vlákna.

Když vytvoříte objekt nebo ovládací prvek pomocí Průvodce přidáním třídy knihovny ATL, průvodce automaticky implementuje podporu registru založenou na skriptech a přidá [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makro do souborů. Pokud nechcete podporu registru založeného na skriptech, je třeba toto makro nahradit DECLARE_REGISTRY. DECLARE_REGISTRY vloží do registru pouze pět výše popsaných základních klíčů. Chcete-li vložit další klíče do registru, je nutné ručně napsat kód.

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Určuje informace potřebné k automatické *registraci appid*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parametry

*Resid*<br/>
ID prostředku souboru RGS, který obsahuje informace o *appid*.

*Appid*<br/>
Identifikátor GUID.

### <a name="remarks"></a>Poznámky

Použijte DECLARE_REGISTRY_APPID_RESOURCEID `CAtlModuleT`v odvozené třídě.

### <a name="example"></a>Příklad

Třídy přidané do projektů ATL pomocí průvodce přidáním kódu třídy budou mít ukázku použití tohoto makra.

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Získá pojmenovaný prostředek obsahující soubor registru a spustí skript pro buď zadávat objekty do systémového registru nebo je odebrat ze systémového registru.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Identifikátor řetězce vašeho prostředku.

### <a name="remarks"></a>Poznámky

Při vytváření objektu nebo ovládacího prvku pomocí Průvodce projektem knihovny ATL průvodce automaticky implementuje podporu registru založenou na skriptech a přidá do souborů [makro DECLARE_REGISTRY_RESOURCEID,](#declare_registry_resourceid) které je podobné DECLARE_REGISTRY_RESOURCE.

Můžete staticky propojit s součástí registru ATL (Registrar) pro optimalizovaný přístup k registru. Chcete-li staticky propojit kód registrátora, přidejte do souboru *pch.h* následující řádek (*stdafx.h* v sadě Visual Studio 2017 a starší):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Pokud chcete, aby společnost ATL nahradila náhradní hodnoty za běhu, nezadávejte DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID makro. Místo toho vytvořte `_ATL_REGMAP_ENTRIES` pole struktur, kde každá položka obsahuje variabilní zástupný symbol spárovaný s hodnotou, která nahradí zástupný symbol za běhu. Potom zavolejte [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), předání pole. Tím se všechny náhradní hodnoty `_ATL_REGMAP_ENTRIES` ve strukturách přidá do náhradní mapy registrátora.

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Součást registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Stejné jako [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) s tím rozdílem, že používá průvodce generované UINT k identifikaci prostředku, spíše než název řetězce.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Identifikátor zdroje generovaný průvodcem.

### <a name="remarks"></a>Poznámky

Při vytváření objektu nebo ovládacího prvku pomocí Průvodce projektem knihovny ATL průvodce automaticky implementuje podporu registru založenou na skriptech a přidá DECLARE_REGISTRY_RESOURCEID makro do souborů.

Můžete staticky propojit s součástí registru ATL (Registrar) pro optimalizovaný přístup k registru. Chcete-li staticky propojit kód registrátora, přidejte do *souboru stdafx.h* následující řádek *(pch.h* v sadě Visual Studio 2019 a novější):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Pokud chcete, aby společnost ATL nahradila náhradní hodnoty za běhu, nezadávejte DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID makro. Místo toho vytvořte `_ATL_REGMAP_ENTRIES` pole struktur, kde každá položka obsahuje variabilní zástupný symbol spárovaný s hodnotou, která nahradí zástupný symbol za běhu. Potom zavolejte [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), předání pole. Tím se všechny náhradní hodnoty `_ATL_REGMAP_ENTRIES` ve strukturách přidá do náhradní mapy registrátora.

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Součást registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
