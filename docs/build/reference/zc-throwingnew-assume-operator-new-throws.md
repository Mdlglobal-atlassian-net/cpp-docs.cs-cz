---
title: /Zc:throwingNew (že operátor new vyvolá výjimku)
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: c8c7b4e7246cc3bb1b3a73cde4f6830eb7178dd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315986"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (že operátor new vyvolá výjimku)

Když **/Zc:throwingNew** je zadána možnost, kompilátor optimalizuje volání `operator new` přeskočit kontroly pro vrácení ukazatel s hodnotou null. Tato možnost instruuje kompilátor, aby předpokládal, že všechny propojené implementace `operator new` a vlastních alokátorů odpovídat standardu jazyka C++ a vyvolat na došlo k chybě přidělení. Ve výchozím nastavení v sadě Visual Studio, vygeneruje kompilátor pessimistically kontroly hodnoty null (**/Zc:throwingNew-**) pro toto volání, protože uživatele můžete propojit s na non-throwing. implementace `operator new` nebo napište vlastní Alokátor rutiny které vracejí ukazatele s hodnotou null.

## <a name="syntax"></a>Syntaxe

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>Poznámky

Od verze ISO C ++ 98, má zadanou standardu, který výchozí [operátor new](../../standard-library/new-operators.md#op_new) vyvolá `std::bad_alloc` při selhání přidělení paměti. Verze aplikace Visual C++ do sady Visual Studio 6.0 vrátí ukazatel s hodnotou null na selhání přidělení. Od sady Visual Studio 2002, `operator new` odpovídá standardu a vyvolá výjimku při selhání. Kód, který používá starší styl přidělení, Visual Studio podporuje propojovací provádění `operator new` v nothrownew.obj, která vrací ukazatel s hodnotou null při selhání. Ve výchozím nastavení vygeneruje kompilátor také obranné kontroly hodnoty null, tyto starší styl alokátorů zabránit způsobí okamžité selhání při selhání. **/Zc:throwingNew** možnost instruuje kompilátor, aby vynechat tyto kontroly hodnoty null, za předpokladu, že všechny propojené paměti alokátorů řídí standardem. Tato akce není požadována k explicitní non-throwing. `operator new` přetížení, které jsou deklarovány pomocí další parametr typu `std::nothrow_t` a používat explicitní `noexcept` specifikace.

Koncepčně, k vytvoření objektu ve volném úložišti, kompilátor vygeneruje kód pro přidělení paměti a potom k vyvolání konstruktoru inicializovat paměť. Protože kompilátor MSVC obvykle nemůže určit-li tento kód se propojí s alokátorem nonkonformní, které nevyvolají, ve výchozím nastavení také vygeneruje kontrolu hodnot null před voláním konstruktoru. To zabraňuje ukazatel s hodnotou null přistoupit přes ukazatel ve volání konstruktoru, pokud selže non-throwing. přidělení. Ve většině případů jsou tyto kontroly nezbytné, protože výchozí `operator new` alokátorů throw místo vrácení ukazatelé s hodnotou null. Kontroly také mít unfortunate vedlejší účinky. Jejich nafouknutí velikost kódu, že vyplnění prediktivní větev a jejich potlačení další optimalizace kompilátoru užitečné například devirtualization nebo const šíření mimo inicializaci objektu. Kontroly k dispozici pouze pro kód podpory, který odkazuje na *nothrownew.obj* nebo má vlastní nonkonformní `operator new` implementace. Pokud nepoužijete nonkonformní `operator new`, doporučujeme použít **/Zc:throwingNew** optimalizaci kódu.

**/Zc:throwingNew** možnost je vypnuto ve výchozím nastavení a nemá vliv [/ permissive-](permissive-standards-conformance.md) možnost.

Pokud kompilujete pomocí generování kódu při propojování (LTCG), není potřeba zadat **/Zc:throwingNew**. Pokud váš kód je zkompilován s použitím LTCG, může kompilátor zjistí, jestli výchozí nastavení, odpovídající `operator new` slouží k implementaci. Pokud ano, kompilátor automaticky vynechány kontroly hodnoty null. Propojovací program vyhledá **/ThrowingNew** příznak zjistit, pokud provádění `operator new` shoduje. Tento příznak do propojovacího programu můžete zadat zahrnutím této směrnice ve zdroji pro novou implementaci vlastní operátor:

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Z **konfigurace** rozevírací nabídku, vyberte **všechny konfigurace**.

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc:throwingNew** nebo **/Zc:throwingNew-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (shoda)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[Specifikace výjimek (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[ukončit (výjimek)](../../standard-library/exception-functions.md#terminate)<br/>
