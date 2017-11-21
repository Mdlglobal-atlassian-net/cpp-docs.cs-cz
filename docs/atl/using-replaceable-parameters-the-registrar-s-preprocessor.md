---
title: "Pomocí nahraditelné parametry (Registrátor ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs: C++
helpviewer_keywords: '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6909db6a68a9e637ed0cf8513f49ba306007ce6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Pomocí nahraditelné parametry (registrátora & č. 39; s Preprocessor)
Nahraditelné parametry Povolit klientům doménového registrátora zadejte data pro spuštění. K tomuto účelu udržuje registrátora nahrazení mapy, do kterého přejde hodnoty přidružené k nahraditelné parametry ve vašem skriptu. Registrátora umožňuje tyto položky v době běhu.  
  
##  <a name="_atl_using_.25.module.25"></a>Pomocí modulu %  
 [Průvodce ovládacím prvkem ATL](../atl/reference/atl-control-wizard.md) automaticky vytvoří skript, který používá `%MODULE%`. ATL používá tento replaceable parametr pro skutečné umístění vašeho serveru knihovny DLL nebo EXE.  
  
## <a name="concatenating-run-time-data-with-script-data"></a>Zřetězení Run-Time dat s daty skriptu  
 Jiné preprocesor slouží k řetězení běhu dat pomocí data skriptu. Předpokládejme například, položka je vyžadována obsahující úplnou cestu k modulu řetězcem "`, 1`" přidán na konec. Nejprve definujte následující rozšíření:  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 Potom před volání jedné skriptu zpracování metody uvedené v [vyvolání skripty](../atl/invoking-scripts.md), přidat náhradní do mapy:  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 Při analýze skript registrátora rozšíří `'%MODULE%, 1'` k `c:\mycode\mydll.dll, 1`.  
  
> [!NOTE]
>  Ve skriptu registrátora 4K je maximální velikost tokenu. (Token je libovolný rozpoznatelném element v syntaxi.) To zahrnuje tokeny, které byly vytvořeny nebo rozšiřovat preprocesor.  
  
> [!NOTE]
>  Pokud chcete nahradit nahrazení hodnoty v době běhu, odeberte volání ve skriptu [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) nebo [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) makro. Místo toho jej nahradit vlastními `UpdateRegistry` metoda, která volá [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) nebo [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)a předejte vaše pole **_ATL_REGMAP_ENTRY** struktury. Vaše pole **_ATL_REGMAP_ENTRY** musí mít minimálně jeden záznam, který je nastaven na {**NULL**,**NULL**}, a tato položka musí být vždy poslední položky. Jinak bude chybu narušení přístupu vygenerované při **UpdateRegistryFromResource** je volána.  
  
> [!NOTE]
>  Při sestavování projektu, který produkuje spustitelný soubor, ATL automaticky přidá uvozovky název cesty vytvořen při běhu pomocí **modulu %** parametr skriptu registrátora. Pokud nechcete, aby název cesty se má použít uvozovky, použít novou **MODULE_RAW %** parametr místo.  
>   
>  Při sestavování projektu, který produkuje knihovny DLL, nebude ATL přidat název cesty uvozovky Pokud **modulu %** nebo **MODULE_RAW %** se používá.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření skripty registrátora](../atl/creating-registrar-scripts.md)

