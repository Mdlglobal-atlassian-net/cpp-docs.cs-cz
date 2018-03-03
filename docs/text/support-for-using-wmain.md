---
title: "Podpora použití funkce wmain | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- wWinMain
dev_langs:
- C++
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 721915ca5ebbc75b17771dae0804e94aa360177c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="support-for-using-wmain"></a>Podpora použití funkce wmain
Visual C++ podporuje definování **wmain** funkce a předání argumentů široká charakterová do vaší aplikace kódování Unicode. Deklarovat formální parametry **wmain**, formátu podobná **hlavní**. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. `argv` a `envp` parametry, které **wmain** typu `wchar_t*`. Příklad:  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  Aplikace MFC Unicode používat **wWinMain –** jako vstupní bod. V takovém případě `CWinApp::m_lpCmdLine` je řetězec znaků Unicode. Nezapomeňte nastavit **wWinMainCRTStartup** s [/Entry](../build/reference/entry-entry-point-symbol.md) – možnost linkeru.  
  
 Pokud váš program používá **hlavní** funkce, vytvoří prostředí vícebajtových znaků běhové knihovny při spuštění programu. Pouze v případě potřeby se vytvoří kopie široká charakterová prostředí (například voláním `_wgetenv` nebo `_wputenv` funkce). Při prvním volání `_wputenv`, nebo při prvním volání `_wgetenv` Pokud prostředí MBCS již existuje, je vytvořit odpovídající prostředí široká charakterová řetězec. Prostředí poté ukazuje `_wenviron` globální proměnná, která je verze široká charakterová z `_environ` – globální proměnná. V tomto okamžiku dvě kopie prostředí (MBCS a Unicode) současně existovat a udržované v běhu systému po celou dobu životnosti programu.  
  
 Podobně pokud váš program používá **wmain** funkce, široká charakterová prostředí se vytvoří při spuštění programu a je na kterou odkazuje `_wenviron` – globální proměnná. Prostředí MBCS (ASCII) je vytvořen při prvním volání `_putenv` nebo `getenv` a ukazuje `_environ` – globální proměnná.  
  
## <a name="see-also"></a>Viz také  
 [Podpora kódování Unicode](../text/support-for-unicode.md)   
 [Souhrn programování Unicode](../text/unicode-programming-summary.md)   
 [WinMain – funkce](http://msdn.microsoft.com/library/windows/desktop/ms633559)