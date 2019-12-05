---
title: 'main: nastavení programu'
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
ms.openlocfilehash: 29e1b77c2e36c66e4e6fc4ec30a73af4d57654a0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857434"
---
# <a name="main-program-startup"></a>main: nastavení programu

Speciální funkce s názvem **Main** je počáteční bod spuštění pro všechny jazyky C a C++ programy. Pokud píšete kód, který odpovídá programovacímu modelu Unicode, můžete použít `wmain`, což je verze **hlavního znaku Main**.

**Hlavní** funkce není předdefinována kompilátorem. Musí být dodán v textu programu.

Syntaxe deklarace pro **Main** je

```cpp
int main();
```

případně můžete také

```cpp
int main(int argc, char *argv[], char *envp[]);
```

**Specifické pro společnost Microsoft**

Syntaxe deklarace pro `wmain` je následující:

```cpp
int wmain( );
```

případně můžete také

```cpp
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Můžete také použít `_tmain`, která je definována v Tchar. h. Pokud není definován _UNICODE, `_tmain` se přeloží na **Main** . V takovém případě `_tmain` přeloží na `wmain`.

Alternativně lze funkce **Main** a `wmain` deklarovat jako vracející **typ void** (žádná návratová hodnota). Pokud deklarujete **Main** nebo `wmain` jako vracející **typ void**, nemůžete vrátit ukončovací kód do nadřazeného procesu nebo operačního systému pomocí příkazu [return](../cpp/return-statement-in-program-termination-cpp.md) . Chcete-li vrátit ukončovací kód v případě, že je **Hlavní** nebo `wmain` deklarován jako **void**, je nutné použít funkci [Exit](../cpp/exit-function.md) .

**Specifické pro konec Microsoftu**

Typy pro `argc` a `argv` jsou definovány jazykem. Názvy `argc`, `argv`a `envp` jsou tradiční, ale nejsou vyžadovány kompilátorem. Další informace a příklad naleznete v tématu [definice argumentů](../cpp/argument-definitions.md).

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Použití funkce wmain namísto main](../cpp/using-wmain-instead-of-main.md)<br/>
[main – omezení funkce](../cpp/main-function-restrictions.md)<br/>
[Analýza argumentů příkazového řádku jazyka C++](../cpp/parsing-cpp-command-line-arguments.md)
