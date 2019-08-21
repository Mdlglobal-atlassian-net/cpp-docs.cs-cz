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
ms.openlocfilehash: c2a70c15473798ba6eb2ef35e0b7ded395708586
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630623"
---
# <a name="registry-macros"></a>Makra registru

Tato makra definují užitečnou knihovnu typů a možnosti registru.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Označuje, že chcete, aby byl registrační kód objektu v objektu, aby nedošlo k závislosti na knihovně ATL. DLL.|
|[DECLARE_LIBID](#declare_libid)|Poskytuje způsob, jak ATL získat *LIBID* knihovny typů.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Vyhněte se výchozí registraci ATL.|
|[DECLARE_REGISTRY](#declare_registry)|Zadá nebo odebere položku hlavního objektu v registru systému.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Určuje informace potřebné k automatické registraci *AppID*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Najde pojmenovaný prostředek a spustí v něm skript registru.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Vyhledá prostředek identifikovaný IDENTIFIKAČNÍm číslem a spustí v něm skript registru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Symbol, který označuje, zda má být registrační kód objektu v objektu, aby se předešlo závislosti na knihovně ATL. DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Poznámky

Při definování ATL_STATIC_REGISTRY byste měli použít následující kód:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>DECLARE_LIBID

Poskytuje způsob, jak ATL získat *LIBID* knihovny typů.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parametry

*LIBID*<br/>
Identifikátor GUID knihovny typů

### <a name="remarks"></a>Poznámky

Použijte DECLARE_LIBID v `CAtlModuleT`odvozené třídě.

### <a name="example"></a>Příklad

Projekty ATL založené na atributech, které nejsou vygenerované pomocí atributů, budou mít ukázku použití tohoto makra.

##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Použijte DECLARE_NO_REGISTRY, pokud chcete zabránit jakémukoli výchozí registraci ATL pro třídu, ve které se toto makro zobrazí.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>DECLARE_REGISTRY

Zadá standardní registraci třídy do systémového registru nebo ji odebere ze systémového registru.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>Parametry

*class*<br/>
pro Zahrnuto z důvodu zpětné kompatibility.

*pid*<br/>
pro LPCTSTR, který je identifikátorem programu specifickým pro verzi.

*vpid*<br/>
pro LPCTSTR, který je identifikátor programu nezávislý na verzi.

*nid*<br/>
pro UINT, který je indexem řetězce prostředku v registru, který se má použít jako popis programu.

*Flag*<br/>
pro Hodnota DWORD obsahující model vláken tohoto programu v registru. Musí být jedna z následujících hodnot: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.

### <a name="remarks"></a>Poznámky

Standardní registrace se skládá z identifikátoru CLSID, ID programu, ID programu nezávislého na verzi, řetězce popisu a modelu vlákna.

Při vytváření objektu nebo ovládacího prvku pomocí Průvodce přidáním třídy ATL Průvodce automaticky implementuje podporu registru založenou na skriptech a přidá do souborů makro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) . Pokud nechcete podporu registru založenou na skriptech, musíte toto makro nahradit pomocí DECLARE_REGISTRY. DECLARE_REGISTRY vloží do registru pouze pět základních klíčů popsaných výše. Je nutné ručně napsat kód pro vložení dalších klíčů do registru.

##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Určuje informace potřebné k automatické registraci *AppID*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parametry

*RESID*<br/>
ID prostředku souboru. rgs, který obsahuje informace o *AppID*.

*appid*<br/>
IDENTIFIKÁTOR GUID.

### <a name="remarks"></a>Poznámky

Použijte DECLARE_REGISTRY_APPID_RESOURCEID v `CAtlModuleT`odvozené třídě.

### <a name="example"></a>Příklad

Třídy přidané do projektů ATL pomocí Průvodce přidáním kódu třídy budou mít ukázku použití tohoto makra.

##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Získá pojmenovaný prostředek obsahující soubor registru a spustí skript pro zadání objektů do systémového registru nebo jejich odebrání ze systémového registru.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
pro Identifikátor řetězce vašeho prostředku

### <a name="remarks"></a>Poznámky

Při vytváření objektu nebo ovládacího prvku pomocí Průvodce projektem ATL Průvodce automaticky implementuje podporu registru založenou na skriptech a přidá makro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) , které je podobně jako DECLARE_REGISTRY_RESOURCE, do souborů.

Pro optimalizovaný přístup k registru můžete staticky propojit komponentu registru ATL (registrátor). Chcete-li staticky propojit kód registrátora, přidejte následující řádek do souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Pokud chcete, aby knihovna ATL nahradila nahrazující hodnoty za běhu, nezadávejte makro DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID. Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každá položka obsahuje zástupný symbol s proměnnou s hodnotou, která nahradí zástupný symbol za běhu. Pak zavolejte [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)a předejte pole. Tím se do náhradní mapy registrátora přidá všechny `_ATL_REGMAP_ENTRIES` nahrazující hodnoty ve strukturách.

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Komponenta registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Stejné jako [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) s tím rozdílem, že používá k identifikaci prostředku objekt uint generovaný průvodcem, nikoli název řetězce.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
pro Identifikátor vygenerovaného průvodcem pro váš prostředek.

### <a name="remarks"></a>Poznámky

Při vytváření objektu nebo ovládacího prvku pomocí Průvodce projektem ATL Průvodce automaticky implementuje podporu registru založenou na skriptech a přidá makro DECLARE_REGISTRY_RESOURCEID do souborů.

Pro optimalizovaný přístup k registru můžete staticky propojit komponentu registru ATL (registrátor). Chcete-li staticky propojit kód registrátora, přidejte následující řádek do souboru *stdafx. h* (*PCH. h* v aplikaci Visual Studio 2019 a novější):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Pokud chcete, aby knihovna ATL nahradila nahrazující hodnoty za běhu, nezadávejte makro DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID. Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každá položka obsahuje zástupný symbol s proměnnou s hodnotou, která nahradí zástupný symbol za běhu. Pak zavolejte [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)a předejte pole. Tím se do náhradní mapy registrátora přidá všechny `_ATL_REGMAP_ENTRIES` nahrazující hodnoty ve strukturách.

Další informace o nahraditelných parametrech a skriptování naleznete v článku [Komponenta registru ATL (registrátor)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Viz také:

[Makr](../../atl/reference/atl-macros.md)
