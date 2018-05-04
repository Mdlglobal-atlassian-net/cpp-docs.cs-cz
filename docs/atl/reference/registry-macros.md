---
title: Makra registru | Microsoft Docs
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
ms.openlocfilehash: ed9b172217f1ca7ada7d8752151126b53055df37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="registry-macros"></a>Makra registru
Tyto makra definovat užitečné typu knihovny a registru zařízení.  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Udává, že kód registrace pro vaše objektu v objektu, aby se zabránilo závislost na ATL. KNIHOVNY DLL.|  
|[DECLARE_LIBID](#declare_libid)|Poskytuje způsob, jak ATL získat *ID knihovny* knihovny typů.|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Zabraňuje výchozí ATL registrace.|  
|[DECLARE_REGISTRY](#declare_registry)|Zadá nebo odebere hlavní objekt záznam v registru systému.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Určuje informace požadované pro automatickou registraci *appid*.|  
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Najde s názvem prostředku a spouští skript registru v něm.|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Najde v prostředku označeném identifikátorem ID číslo a spouští skript registru v něm.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
    
##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY  
 Symbol, který označuje, že chcete kód registrace pro vaše objektu v objektu, aby se zabránilo závislost na ATL. KNIHOVNY DLL.  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>Poznámky  
 Když definujete **ATL_STATIC_REGISTRY**, měli byste použít následující kód:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>  DECLARE_LIBID  
 Poskytuje způsob, jak ATL získat *ID knihovny* knihovny typů.  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>Parametry  
 *ID knihovny*  
 Identifikátor GUID knihovny typů.  
  
### <a name="remarks"></a>Poznámky  
 Použití `DECLARE_LIBID` v `CAtlModuleT`-odvozené třídy.  
  
### <a name="example"></a>Příklad  
 Projekty knihovny ATL s atributy bez vygenerované průvodcem bude mít ukázce použití této makra.  
  
##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY  
 Použití `DECLARE_NO_REGISTRY` Pokud chcete, aby se zabránilo žádné výchozí ATL registrace pro třídu, ve kterém se zobrazí tato makro.  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>  DECLARE_REGISTRY  
 Zadá registrace standardní třídy do registru systému nebo odebere z registru systému.  
  
```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```  
  
### <a name="parameters"></a>Parametry  
 `class`  
 [v] Zahrnuté z důvodu zpětné kompatibility.  
  
 `pid`  
 [v] `LPCTSTR` Tedy identifikátor specifické pro verzi programu.  
  
 *vpid*  
 [v] `LPCTSTR` Tedy identifikátor nezávislé na verzi programu.  
  
 *nID*  
 [v] A **Celé_číslo** tedy indexu řetězec prostředku v registru, který chcete použít jako popis programu.  
  
 `flags`  
 [v] A `DWORD` obsahující program modelu v registru vláken. Musí mít jednu z následujících hodnot: **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, nebo **AUTPRXFLAG**.  
  
### <a name="remarks"></a>Poznámky  
 Standardní registrace se skládá z CLSID, ID programu, ID programu nezávislé na verzi, řetězec popisu a model vláken.  
  
 Při vytvoření objektu nebo řízení pomocí Průvodce přidáním třídy ATL, průvodce automaticky implementuje podporu založených na skriptech registru a přidá [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makro k souborům. Pokud nechcete, aby založených na skriptech registru podpory, budete muset nahraďte tento makro s `DECLARE_REGISTRY`. `DECLARE_REGISTRY` Vloží pouze pět základní klíče do registru popsané výše. Musíte ručně napsat kód pro vložení jiných klíčů do registru.  
  
##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID  
 Určuje informace požadované pro automatickou registraci *appid*.  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>Parametry  
 *resid*  
 Id prostředku s informacemi o souboru *appid*.  
  
 *AppID*  
 IDENTIFIKÁTOR GUID.  
  
### <a name="remarks"></a>Poznámky  
 Použití `DECLARE_REGISTRY_APPID_RESOURCEID` v `CAtlModuleT`-odvozené třídy.  
  
### <a name="example"></a>Příklad  
 Třídy pro projekty knihovny ATL přidané pomocí průvodce Přidat třídu kód bude mít ukázce použití této makra.  
  
##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE  
 Získá obsahující soubor registru s názvem prostředku a spustí skript, který chcete zadat objekty do registru systému nebo je odebrat z registru systému.  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Řetězec identifikátor prostředku.  
  
### <a name="remarks"></a>Poznámky  
 Při vytvoření objektu nebo řízení pomocí Průvodce projektu knihovny ATL, průvodce automaticky implementovat podporu založených na skriptech registru a přidat [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makro, které je podobné `DECLARE_REGISTRY_RESOURCE`do vaší soubory.  
  
 Staticky můžete propojit s komponenta knihovny ATL registru (Registrar) pro přístup k registru optimalizované. Staticky propojit s kód registrátora, přidejte následující řádek do souboru stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Pokud chcete, aby ATL k nahrazení hodnoty nahraďte v době běhu, nezadávejte `DECLARE_REGISTRY_RESOURCE` nebo `DECLARE_REGISTRY_RESOURCEID` makro. Místo toho vytvořte pole **_ATL_REGMAP_ENTRIES** struktury, kde každý záznam obsahuje zástupný symbol proměnné spárovat s hodnotou pro nahraďte zástupný symbol v době běhu. Potom zavolejte [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), předávání pole. Tento postup přidá všechny nahrazení hodnoty v **_ATL_REGMAP_ENTRIES** struktury vašeho registrátora nahrazení mapu.  

  
 Další informace o nahraditelné parametry a skriptování, najdete v článku [ATL komponenta registru (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID  
 Stejné jako [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) s tím rozdílem, že používá vygenerované průvodcem **Celé_číslo** k identifikaci prostředku, nikoli název řetězce.  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [v] Generované průvodcem identifikátor prostředku.  
  
### <a name="remarks"></a>Poznámky  
 Při vytvoření objektu nebo řízení pomocí Průvodce projektu knihovny ATL, průvodce automaticky implementovat podporu založených na skriptech registru a přidat `DECLARE_REGISTRY_RESOURCEID` makro k souborům.  
  
 Staticky můžete propojit s komponenta knihovny ATL registru (Registrar) pro přístup k registru optimalizované. Staticky propojit s kód registrátora, přidejte následující řádek do souboru stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Pokud chcete, aby ATL k nahrazení hodnoty nahraďte v době běhu, nezadávejte `DECLARE_REGISTRY_RESOURCE` nebo `DECLARE_REGISTRY_RESOURCEID` makro. Místo toho vytvořte pole **_ATL_REGMAP_ENTRIES** struktury, kde každý záznam obsahuje zástupný symbol proměnné spárovat s hodnotou pro nahraďte zástupný symbol v době běhu. Potom zavolejte [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), předávání pole. Tento postup přidá všechny nahrazení hodnoty v **_ATL_REGMAP_ENTRIES** struktury vašeho registrátora nahrazení mapu.  

  
 Další informace o nahraditelné parametry a skriptování, najdete v článku [ATL komponenta registru (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
