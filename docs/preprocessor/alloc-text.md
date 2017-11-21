---
title: "alloc_text – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
dev_langs: C++
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e877f747bc825faac38c3557b52e0f0969257208
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alloctext"></a>alloc_text
Pojmenuje oddíl kódu, do kterého mají být umístěny dané definice funkcí. Pro pojmenované funkce se tato direktiva pragma musí vyskytnout mezi deklarátorem funkce a její definicí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma alloc_text( "  
textsection  
", function1, ... )  
```  
  
## <a name="remarks"></a>Poznámky  
 **Alloc_text –** – Direktiva pragma nezpracovává C++ členské funkce nebo přetížených funkcí. Se vztahuje pouze na funkce deklarovat s propojení C – to znamená, funkce deklarovat s **extern "C"** specifikaci propojení. Při pokusu o použití této direktivy pragma u funkce s propojením jazyka C++ dojde k vygenerování chyby kompilátoru.  
  
 Od funkce adresování pomocí `__based` nepodporuje zadání umístění části vyžaduje použití **alloc_text –** – Direktiva pragma. Název zadaný *textsection* musí být uzavřena v uvozovkách.  
  
 **Alloc_text –** – Direktiva pragma musí následovat za deklarace všech určených funkcí a před definice tyto funkce.  
  
 Funkce, kterou se odkazuje v **alloc_text –** – Direktiva pragma by měl být definován ve stejném modulu, jako – Direktiva pragma. Pokud tato podmínka není splněna a dojde-li později ke kompilaci nedefinované funkce do jiné textové části, zachycení této chyby není zaručeno. Ačkoli program bude obvykle fungovat správně, nebude funkce přidělena ve správném oddílu.  
  
 Další omezení **alloc_text –** jsou následující:  
  
-   Nelze ji použít uvnitř funkce.  
  
-   Musí být použita po deklaraci funkce, ale před její definicí.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)