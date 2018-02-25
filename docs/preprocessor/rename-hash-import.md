---
title: "Přejmenovat (#import) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6391f3d88a081da6e01b115389b1a9b986ae6c0f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="rename-import"></a>rename (#import)
**Konkrétní C++**  
  
 Funguje kolem název kolizí problémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
rename("OldName","NewName")  
```  
  
#### <a name="parameters"></a>Parametry  
 `OldName`  
 Původní název v knihovně typů.  
  
 `NewName`  
 Název má být použit místo starý název.  
  
## <a name="remarks"></a>Poznámky  
 Pokud tento atribut je zadán, kompilátor nahradí všechny výskyty *OldName* v knihovně typů s uživatelem zadané *NewName* v výsledné soubory hlaviček.  
  
 Tento atribut lze při název typu knihovny se shoduje s definici makra v systémových souborech záhlaví. Pokud tato situace nevyřeší, pak různé chyby syntaxe se budou generovat, jako například [C2059 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2059.md) a [C2061 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2061.md).  
  
> [!NOTE]
>  Nahrazení je název sloužící v knihovny typů, ne pro název používaný v výsledný soubor hlaviček.  
  
 Předpokládejme například, vlastnost s názvem `MyParent` existuje v knihovny typů a makra `GetMyParent` je definována v záhlaví souboru a použít před `#import`. Vzhledem k tomu `GetMyParent` je výchozí název funkce obálku pro zpracování chyb **získat** vlastnost, dojde k kolize názvů. Pokud chcete tento problém obejít, použijte následující atribut v `#import` příkaz:  
  
```  
rename("MyParent","MyParentX")  
```  
  
 které přejmenuje název `MyParent` v knihovně typů. Pokus o přejmenování `GetMyParent` obálku název selžou:  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
 Důvodem je, že název `GetMyParent` dochází pouze v výsledné hlavičkový soubor knihovny typů.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)