---
title: Použití nahraditelných parametrů (Registrátor ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs:
- C++
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd07a96feae192bd2235b5621da6fe42666280bd
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849494"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Použití nahraditelných parametrů (doménový Registrátor&#39;s preprocesoru)
Nahraditelné parametry umožňují klienta vašeho registrátora zadání dat za běhu. K tomuto účelu udržuje doménový Registrátor nahrazení mapování, do kterého se zadá hodnoty přidružené k nahraditelné parametry ve skriptu. Doménový Registrátor provede tyto položky v době běhu.  
  
##  <a name="_atl_using_.25.module.25"></a> Pomocí modulu %  
 [Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md) automaticky generuje skript, který používá `%MODULE%`. ATL – používá tuto proměnnou pro skutečné umístění souboru EXE nebo knihovny DLL váš server.  
  
## <a name="concatenating-run-time-data-with-script-data"></a>Zřetězení dat za běhu pomocí Data skriptu  
 Další možností použití preprocesoru je zřetězit data za běhu s daty skriptu. Předpokládejme například, že položka je potřeba, který obsahuje úplnou cestu k modulu s řetězcem "`, 1`" přidán na konec. Nejprve definujte následující rozšíření:  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 Potom jeden skript zpracování metody uvedené v před voláním [vyvolání skriptů](../atl/invoking-scripts.md), přidejte můžou nahradit aktuální soubor do mapy:  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 Při analýze souboru, který rozbalí doménový Registrátor `'%MODULE%, 1'` k `c:\mycode\mydll.dll, 1`.  
  
> [!NOTE]
>  Ve skriptu registrátoru je 4 kB maximální velikost tokenu. (Token je libovolný prvek rozpoznat v syntaxi). To zahrnuje tokeny, které byly vytvořeny nebo analyzována pomocí preprocesoru.  
  
> [!NOTE]
>  Nahradit nahrazujícími hodnotami v době běhu, odeberte volání ve skriptu na [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) – makro. Místo toho, nahraďte ho vlastním `UpdateRegistry` metodu, která volá [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)a předat vaše pole _ATL_REGMAP_ Položka struktury. Vaše pole _ATL_REGMAP_ENTRY musí mít alespoň jednu položku, která je nastavena na {NULL, NULL} a tato položka by měla být vždy poslední položky. V opačném případě chybu narušení přístupu bude generována v případě `UpdateRegistryFromResource` je volána.  
  
> [!NOTE]
>  Při sestavování projektu, jejichž výstupem jsou spustitelný soubor, ATL automaticky přidá uvozovky kolem názvu cesty vytvořen v době běhu s **modulu %** parametr skriptu doménový Registrátor. Pokud nechcete, aby se název cesty do uvozovek, pomocí nové **MODULE_RAW %** parametr místo.  
>   
>  Při sestavování projektu, jejichž výstupem jsou knihovny DLL, ATL nebude přidávat uvozovky název cesty, pokud **modulu %** nebo **MODULE_RAW %** se používá.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)

