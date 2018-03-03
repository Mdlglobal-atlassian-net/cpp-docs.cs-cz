---
title: "-sdl (povolit další kontroly zabezpečení) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
dev_langs:
- C++
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbcb74272fa7cae3dd0c641bd6371c8f0f9c204
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (Povolit další kontroly zabezpečení)
Přidá doporučené kontroly životního cyklu SDL (Security Development). Tyto kontroly zahrnovat velmi důležité pro zabezpečení upozornění jako chyby a další bezpečné generování kódu funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/sdl[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 **SDL** umožňuje nadmnožinou směrného plánu kontrol zabezpečení poskytované [/GS](../../build/reference/gs-buffer-security-check.md) a přepíše **/GS-**. Ve výchozím nastavení **SDL** je vypnutý. **/SDL-** zakáže další kontroly zabezpečení.  
  
## <a name="compile-time-checks"></a>Kompilace kontroly  
 **SDL** umožňuje tyto upozornění jako chyby:  
  
|Upozornění ve SDL povoleno|Ekvivalentní přepínač příkazového řádku|Popis|  
|------------------------------|-------------------------------------|-----------------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Unární mínus – operátor bylo použito pro typ bez znaménka, výsledkem je výsledek bez znaménka.|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Záporné integrální konstanta převést na typu bez znaménka, výsledkem je pravděpodobně smysl výsledek.|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Použití `continue`, `break` nebo `goto` klíčová slova v `__finally` / `finally` bloku je nedefinovaný chování při abnormální ukončení.|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Kód inicializace proměnné nebudou provedeny.|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Použijte neinicializované místní proměnné.|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Použití proměnné potenciálně Neinicializovaný místní ukazatele.|  
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Přetečení v případě konkrétních funkcí jazyka C Runtime (CRT) používají vyrovnávací paměti.|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Použití funkce označené – Direktiva pragma [zastaralé](../../preprocessor/deprecated-c-cpp.md).|  
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Použití funkce označen jako [zastaralé](../../cpp/deprecated-cpp.md).|  
  
## <a name="runtime-checks"></a>Kontroly runtime  
 Když **SDL** je povoleno, kompilátor generuje kód k provedení těchto kontrol za běhu:  
  
-   Striktní režim umožňuje **/GS** detekce přetečení vyrovnávací paměti běhu, ekvivalentní kompilujete s `#pragma strict_gs_check(push, on)`.  
  
-   Provede čištění omezené ukazatele. Ve výrazech, které nezahrnují dereferences a typy, které mají žádné uživatelem definované destruktor, jsou odkazy na ukazatele nastavena na neplatné adresu po volání `delete`. To pomáhá zabránit opětovnému použití zastaralých ukazatel odkazy.  
  
-   Provede inicializaci člena třídy. Automaticky inicializuje všichni členové třídy nule při vytváření instance objektu (před spuštěním konstruktoru). To pomáhá zabránit používání Neinicializovaný data přidružená k členy třídy, které konstruktoru neinicializuje explicitně.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [upozornění, SDL a zlepšení Neinicializovaný proměnné detekce](http://go.microsoft.com/fwlink/p/?LinkId=331012).  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Na **Obecné** vyberte tuto možnost z **SDL kontroly** rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)