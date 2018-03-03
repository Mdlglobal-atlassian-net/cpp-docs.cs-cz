---
title: "Použití funkce wmain namísto main | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- wmain
dev_langs:
- C++
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d43ab12c42315d735220af8f91c40d8b6a5cc4f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-wmain-instead-of-main"></a>Použití funkce wmain namísto main
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 V kódu Unicode programovací model, můžete definovat široká charakterová verzi **hlavní** funkce. Použití **wmain** místo **hlavní** Pokud chcete napsat přenosné kód, který dodržuje specifikaci kódování Unicode.  
  
 Deklarovat formální parametry **wmain** pomocí podobném formátu **hlavní**. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. `argv` a `envp` parametry, které **wmain** typu `wchar_t*`.  
  
 Pokud váš program používá **hlavní** funkce, operační systém při spuštění programu je vytvořit prostředí vícebajtových znaků. Pouze v případě potřeby se vytvoří kopie široká charakterová prostředí (například voláním [_wgetenv –](../c-runtime-library/reference/getenv-wgetenv.md) nebo [_wputenv –](../c-runtime-library/reference/putenv-wputenv.md) funkce). Existuje-li již prostředí MBCS, je při prvním volání `_wputenv` nebo při prvním volání `_wgetenv` vytvořeno odpovídající prostředí řetězce širokého znaku, na které je následně odkázáno pomocí globální proměnné `_wenviron`, což je verze širokého znaku globální proměnné `_environ`. V tomto okamžiku vedle sebe existují dvě kopie prostředí (znaková sada MBCS a Unicode), které jsou udržovány v operačním systému po celou dobu trvání aplikace.  
  
 Podobně pokud váš program používá **wmain** funkce, prostředí MBCS (ASCII) je vytvořen při prvním volání `_putenv` nebo `getenv`a je na kterou odkazuje `_environ` – globální proměnná.  
  
 Další informace o rozhraní MBCS prostředí najdete v tématu [jednobajtové a vícebajtové znakové sady](../c-runtime-library/single-byte-and-multibyte-character-sets.md) v *referenční dokumentace běhové knihovny.*  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)