---
title: 'hlavní: Spuštění programu'
ms.date: 11/04/2016
f1_keywords:
- vc.main.startup
- _tmain
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
ms.openlocfilehash: 358ae8ec88281bab741393b1196ee2a1e615e896
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345041"
---
# <a name="main-program-startup"></a>hlavní: Spuštění programu

Speciální funkce s názvem **hlavní** je výchozím bodem provádění všech programů jazyka C a C++. Pokud jste psaní kódu, který splňuje programovací model Unicode, můžete použít `wmain`, což je verze širokého znaku **hlavní**.

**Hlavní** není kompilátorem předdefinované funkce. Musí být zadána textu programu.

Syntaxe deklarace pro **hlavní** je

```cpp
int main();
```

nebo v případě potřeby

```cpp
int main(int argc, char *argv[], char *envp[]);
```

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Syntaxe deklarace pro `wmain` vypadá takto:

```cpp
int wmain( );
```

nebo v případě potřeby

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Můžete také použít `_tmain`, která je definovaná v souboru tchar.h. `_tmain` přeloží na **hlavní** Pokud _UNICODE je definována. V takovém případě `_tmain` přeloží na `wmain`.

Další možností **hlavní** a `wmain` funkce mohou být deklarovány jako návratová **void** (žádnou návratovou hodnotu). Pokud deklarujete **hlavní** nebo `wmain` jako vracející **void**, nejde vrátit kód ukončení nadřazenému procesu nebo operačního systému pomocí [vrátit](../cpp/return-statement-in-program-termination-cpp.md) příkazu. Vrátit východ kódu, kdy **hlavní** nebo `wmain` je deklarován jako **void**, je nutné použít [ukončit](../cpp/exit-function.md) funkce.

**Specifické pro END Microsoft**

Typy pro `argc` a `argv` jsou definovány jazykem. Názvy `argc`, `argv`, a `envp` tradičních, avšak nemusejí kompilátorem. Další informace a příklad najdete v tématu [definice argumentů](../cpp/argument-definitions.md).

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Použití funkce wmain namísto main](../cpp/using-wmain-instead-of-main.md)<br/>
[main – omezení funkce](../cpp/main-function-restrictions.md)<br/>
[Analýza argumentů příkazového řádku jazyka C++](../cpp/parsing-cpp-command-line-arguments.md)
