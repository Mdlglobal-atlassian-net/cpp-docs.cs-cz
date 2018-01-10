---
title: "Použití funkce wmain | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47340642a8c18adfe5e371baca8daca7bd22f28d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-wmain"></a>Používání výrazu wmain
**Konkrétní Microsoft**  
  
 V kódu Unicode programovací model, můžete definovat široká charakterová verzi **hlavní** funkce. Použití **wmain** místo **hlavní** Pokud chcete napsat přenosné kód, který dodržuje Unicode programovací model.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Deklarovat formální parametry **wmain** pomocí podobném formátu **hlavní**. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. `argv` a `envp` parametry, které **wmain** typu `wchar_t*`. Příklad:  
  
 Pokud váš program používá **hlavní** funkce, vytvoří prostředí vícebajtových znaků běhové knihovny při spuštění programu. Pouze v případě potřeby se vytvoří kopie široká charakterová prostředí (například voláním `_wgetenv` nebo `_wputenv` funkce). Existuje-li již prostředí MBCS, je při prvním volání `_wputenv` nebo při prvním volání `_wgetenv` vytvořeno odpovídající prostředí řetězce širokého znaku, na které je následně odkázáno pomocí globální proměnné `_wenviron`, což je verze širokého znaku globální proměnné `_environ`. V tomto okamžiku vedle sebe existují dvě kopie prostředí (znaková sada MBCS a Unicode), které jsou udržovány v operačním systému po celou dobu trvání aplikace.  
  
 Podobně pokud váš program používá **wmain** funkce, široká charakterová prostředí se vytvoří při spuštění programu a je na kterou odkazuje `_wenviron` – globální proměnná. Prostředí MBCS (ASCII) je vytvořen při prvním volání `_putenv` nebo `getenv`a je na kterou odkazuje `_environ` – globální proměnná.  
  
 Další informace o rozhraní MBCS prostředí najdete v tématu [internacionalizace](../c-runtime-library/internationalization.md) v *referenční dokumentace běhové knihovny.*  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)