---
title: -sdl (povolení dalších kontrol zabezpečení) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
dev_langs:
- C++
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6f88e254a49309c0ca44c330fdc71d32ee1a87d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686336"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (Povolit další kontroly zabezpečení)
Přidá doporučené kontroly Security Development Lifecycle (SDL). Mezi tyto kontroly patří velmi týkajících se zabezpečení upozornění jako chyby a další zabezpečené generování kódu funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/sdl[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ SDL** umožňuje nadmnožinou směrného plánu kontrol zabezpečení poskytované [/GS](../../build/reference/gs-buffer-security-check.md) a přepíše **/GS-**. Ve výchozím nastavení **/SDL** je vypnuté. **/SDL-** zakáže další bezpečnostní kontroly.  
  
## <a name="compile-time-checks"></a>Kontroly za kompilace  
 **/ SDL** umožňuje tato upozornění jako chyby:  
  
|Upozornění zajišťuje/SDL|Ekvivalentní přepínač příkazového řádku|Popis|  
|------------------------------|-------------------------------------|-----------------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Unární operátor minus byla použita pro typ bez znaménka, což vede k výsledek bez znaménka.|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Záporná integrální konstantou je převést na typ bez znaménka, výsledkem je pravděpodobně nemá význam výsledek.|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Použití `continue`, `break` nebo `goto` klíčových slov v `__finally` / `finally` blok má během abnormální ukončení nedefinované chování.|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Inicializace proměnné kódu nebude provedeno.|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Použití neinicializovaná lokální proměnná.|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Použití potenciálně neinicializovaná lokální proměnná ukazatele.|  
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Přetečení v případě konkrétních funkcí jazyka C za běhu (CRT) používají vyrovnávací paměti.|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Použití funkce označené – Direktiva pragma [zastaralé](../../preprocessor/deprecated-c-cpp.md).|  
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Použití funkce označené jako [zastaralé](../../cpp/deprecated-cpp.md).|  
  
## <a name="runtime-checks"></a>Kontroly za běhu  
 Když **/SDL** je povoleno, kompilátor vygeneruje kód k provedení těchto kontrol za běhu:  
  
-   Povolí striktní režim **/GS** detekci přetečení vyrovnávací paměti za běhu, ekvivalentní kompilace s `#pragma strict_gs_check(push, on)`.  
  
-   Provádí sanitizace omezené ukazatele. Ve výrazech, které nezahrnují přístupů přes ukazatel, a v typy, které mají žádný uživatelem definovaný destruktor, odkazy na ukazatele nastavte k neplatné adrese po volání `delete`. To pomáhá zabránit opětovnému použití zastaralé ukazatele odkazů.  
  
-   Provede inicializaci členů třídy. Automaticky inicializuje všechny členy třídy na hodnotu nula při vytváření instance objektu (před spuštěním konstruktoru). To pomáhá zabránit používání neinicializovaná data související s členy třídy, které konstruktor explicitně neinicializuje.  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [upozornění, / SDL a zlepšení neinicializované proměnné detekce](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Na **Obecné** stránky, vyberte možnost z **kontroly SDL** rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)