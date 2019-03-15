---
title: /sdl (Povolit další kontroly zabezpečení)
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: 0618b796d492395c3e0e5413047ac0260082baff
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814199"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (Povolit další kontroly zabezpečení)

Přidá doporučené kontroly Security Development Lifecycle (SDL). Mezi tyto kontroly patří velmi týkajících se zabezpečení upozornění jako chyby a další zabezpečené generování kódu funkce.

## <a name="syntax"></a>Syntaxe

```
/sdl[-]
```

## <a name="remarks"></a>Poznámky

**/ SDL** umožňuje nadmnožinou směrného plánu kontrol zabezpečení poskytované [/GS](gs-buffer-security-check.md) a přepíše **/GS-**. Ve výchozím nastavení **/SDL** je vypnuté. **/SDL-** zakáže další bezpečnostní kontroly.

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

- Povolí striktní režim **/GS** detekci přetečení vyrovnávací paměti za běhu, ekvivalentní kompilace s `#pragma strict_gs_check(push, on)`.

- Provádí sanitizace omezené ukazatele. Ve výrazech, které nezahrnují přístupů přes ukazatel, a v typy, které mají žádný uživatelem definovaný destruktor, odkazy na ukazatele nastavte k neplatné adrese po volání `delete`. To pomáhá zabránit opětovnému použití zastaralé ukazatele odkazů.

- Provede inicializaci ukazatele člena třídy. Automaticky inicializuje členy typu ukazatele na třídy **nullptr** při vytváření instance objektu (před spuštěním konstruktoru). To pomáhá zabránit použití neinicializovaného ukazatele, které konstruktor explicitně neinicializuje. Inicializace ukazatele kompilátorem generované členské nazývá tak dlouho, dokud:

  - Objekt není přidělena pomocí vlastní (definovaný uživatelem) `operator new`

  - Objekt není přidělená jako součást pole (například `new A[x]`)

  - Třída není spravované ani importován

  - Třída má uživatelem definovaný výchozí konstruktor.

  Chcete-li inicializovat pomocí funkce inicializace kompilátorem generované třídy, musí být členem ukazatel a není vlastnost nebo – konstanta.

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [upozornění, / SDL a zlepšení neinicializované proměnné detekce](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/).

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Na **Obecné** stránky, vyberte možnost z **kontroly SDL** rozevíracího seznamu.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
