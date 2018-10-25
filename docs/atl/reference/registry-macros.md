---
title: Makra registru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c10908454252b1ae381a2b96835ce09f3aa6db6f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053653"
---
# <a name="registry-macros"></a>Makra registru

Tato makra definují užitečné typ knihovny a registru zařízení.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Určuje, že má být registrační kód pro váš objekt mohl být v objektu, aby se zabránilo závislosti na knihovně ATL. KNIHOVNY DLL.|
|[DECLARE_LIBID](#declare_libid)|Poskytuje způsob, jak získat ATL *libid* knihovny typů.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Zabraňuje výchozí knihovny ATL registrací.|
|[DECLARE_REGISTRY](#declare_registry)|Zadá nebo odebere položky hlavní objekt v systémovém registru.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Určuje informace požadované pro automatickou registraci *appid*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Pojmenovaný prostředek vyhledá a spustí skript registru v rámci něj.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Vyhledá prostředku označeném identifikátorem identifikační číslo a spustí skript registru v rámci něj.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY

Symbol, který označuje, že chcete registrační kód pro váš objekt mohl být v objektu, aby se zabránilo závislosti na knihovně ATL. KNIHOVNY DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Poznámky

Při definování ATL_STATIC_REGISTRY byste měli použít následující kód:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>  DECLARE_LIBID

Poskytuje způsob, jak získat ATL *libid* knihovny typů.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parametry

*ID knihovny*<br/>
Identifikátor GUID knihovny typů.

### <a name="remarks"></a>Poznámky

Použít DECLARE_LIBID v `CAtlModuleT`-odvozené třídy.

### <a name="example"></a>Příklad

Ukázkový používání tohoto makra bude mít projektů knihovny ATL s atributy bez generované v průvodci.

##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY

DECLARE_NO_REGISTRY použijte, pokud chcete, aby se zabránilo registrace všechny výchozí knihovny ATL pro třídy, ve kterém se zobrazí toto makro.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>  DECLARE_REGISTRY

Zadá standardní třídu zápisu do systémového registru nebo ji odebere z registru systému.

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
[in] Zahrnuto z důvodu zpětné kompatibility.

*Identifikátor PID*<br/>
[in] LPCTSTR, který je identifikátor specifické pro verzi programu.

*vpid*<br/>
[in] LPCTSTR, který je identifikátor nezávislé na verzi programu.

*nID*<br/>
[in] UINT, který je index řetězec prostředku v registru, který se použije jako popis programu.

*příznaky*<br/>
[in] Hodnota DWORD obsahující model vláken programu v registru. Musí být jedna z následujících hodnot: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH nebo AUTPRXFLAG.

### <a name="remarks"></a>Poznámky

Standardní zápis se skládá z CLSID, ID programu, ID verze nezávislé na program, řetězec s popisem a model vláken.

Při vytváření objektu nebo ovládací prvek pomocí Průvodce přidáním třídy ATL, průvodce automaticky implementuje podporu založených na skriptech registru a přidá [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) – makro k souborům. Pokud nechcete, aby podpora založených na skriptech registru, musíte DECLARE_REGISTRY nahraďte toto makro. DECLARE_REGISTRY vloží pouze pět základních klíčů výše popsané do registru. Musíte ručně napsat kód k vložení jiných klíčů do registru.

##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID

Určuje informace požadované pro automatickou registraci *appid*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parametry

*resid*<br/>
Id prostředku, který obsahuje informace o souboru .rgs *appid*.

*ID aplikace*<br/>
IDENTIFIKÁTOR GUID.

### <a name="remarks"></a>Poznámky

Použít DECLARE_REGISTRY_APPID_RESOURCEID v `CAtlModuleT`-odvozené třídy.

### <a name="example"></a>Příklad

Třídy přidané do projektů knihovny ATL pomocí průvodce Přidat třídu kód bude mít ukázkový používání tohoto makra.

##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE

Načte pojmenovaný prostředek obsahující soubor registru a spustí skript, který chcete zadat objekty do systémového registru nebo je odeberte ze systémového registru.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Identifikátor prostředku řetězce.

### <a name="remarks"></a>Poznámky

Při vytváření objektu nebo ovládací prvek pomocí Průvodce projektem ATL, průvodce automaticky implementovat podporu založených na skriptech registru a přidat [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) – makro, které se podobá DECLARE_REGISTRY_ PROSTŘEDEK k souborům.

Můžete staticky propojit s komponenta knihovny ATL registru (Registrar) pro přístup k registru optimalizované. Pokud chcete staticky propojit na kód registrátoru, přidejte následující řádek do souboru stdafx.h:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Pokud chcete knihovny ATL pro nahrazení nahrazujícími hodnotami v době běhu, nezadávejte DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID – makro. Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každý záznam obsahuje zástupný symbol proměnné souřadnicí hodnotu nahraďte zástupný text v době běhu. Poté zavolejte [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), předá pole. Tento postup přidá všechny hodnoty nahrazení v `_ATL_REGMAP_ENTRIES` struktury do vašeho registrátora nahrazení mapy.

Další informace o nahraditelné parametry a skriptů, najdete v článku [The komponenta knihovny ATL registru (Registrar)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID

Stejné jako [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) s tím rozdílem, že používá UINT generované v průvodci k identifikaci prostředku, nikoli název řetězce.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Generované průvodcem identifikátor prostředku.

### <a name="remarks"></a>Poznámky

Při vytváření objektu nebo ovládací prvek s použitím Průvodce projektem ATL, průvodce automaticky implementovat podporu založených na skriptech registru a přidá dané makro DECLARE_REGISTRY_RESOURCEID k souborům.

Můžete staticky propojit s komponenta knihovny ATL registru (Registrar) pro přístup k registru optimalizované. Pokud chcete staticky propojit na kód registrátoru, přidejte následující řádek do souboru stdafx.h:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Pokud chcete knihovny ATL pro nahrazení nahrazujícími hodnotami v době běhu, nezadávejte DECLARE_REGISTRY_RESOURCE nebo DECLARE_REGISTRY_RESOURCEID – makro. Místo toho vytvořte pole `_ATL_REGMAP_ENTRIES` struktur, kde každý záznam obsahuje zástupný symbol proměnné souřadnicí hodnotu nahraďte zástupný text v době běhu. Poté zavolejte [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), předá pole. Tento postup přidá všechny hodnoty nahrazení v `_ATL_REGMAP_ENTRIES` struktury do vašeho registrátora nahrazení mapy.

Další informace o nahraditelné parametry a skriptů, najdete v článku [The komponenta knihovny ATL registru (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
