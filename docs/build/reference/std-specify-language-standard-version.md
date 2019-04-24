---
title: / STD (určení standardní jazykové verze)
ms.date: 11/26/2018
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 32c63240f578b6170ae351cdf0cd1628167464b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317884"
---
# <a name="std-specify-language-standard-version"></a>/ STD (určení standardní jazykové verze)

Povolit podporovány funkcí jazyka C++ z určenou verzi standard jazyka C++.

## <a name="syntax"></a>Syntaxe

> / std:\[c ++ 14\|c ++ 17\|c ++ latest]

## <a name="remarks"></a>Poznámky

**/Std** možnost je k dispozici v sadě Visual Studio 2017 a novější. Používá se k řízení programovací jazyk standardní funkce povolené během kompilace kódu specifické pro verzi ISO C++. Tato možnost umožňuje zakázat podporu pro některé nové funkce jazyka a knihovny, které mohou přestat fungovat existující kód, který odpovídá konkrétní verzi jazyka standard. Ve výchozím nastavení **/std: c ++ 14** není zadána, která zakáže jazyka a funkce standardní knihovny, které jsou součástí standardní novější verze jazyka C++. Použití **/std: c ++ 17** povolení C ++ 17 specifické pro standardní funkce a chování. Chcete-li explicitně povolit aktuální implementace kompilátoru a standardní knihovny funkce navrhuje se pro následující normy, použijte **/std: c ++ nejnovější**.

Výchozí hodnota **/std: c ++ 14** možnost povolí sadu funkcí C ++ 14 implementované kompilátorem MSVC. Tato možnost zakáže kompilátoru a standardní knihovny podpora pro funkce, které se mění nebo nové v novějších verzích jazyka standard, s výjimkou některé funkce C ++ 17 již implementováno v předchozích verzích a kompilátorem MSVC. Aby se zabránilo zásadní změny pro uživatele, kteří už udělali závislosti na funkcích, které jsou k dispozici od verze Visual Studio 2015 Update 2, tyto funkce zůstat zapnuté, kdy **/std: c ++ 14** je zadána možnost:

- [Pravidla pro automatické s braced-init-lists](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [TypeName v šabloně parametrů šablony](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Odebrání trigraphs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atributy pro obory názvů a enumerátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [U8 znakové literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Další informace o jaké funkce C ++ 14 a C ++ 17 jsou povolené při **/std: c ++ 14** je zadán, naleznete v části poznámky v [shoda jazyka Visual C++](../../overview/visual-cpp-language-conformance.md).

**/Std: c ++ 17** možnost povolí úplnou sadu funkcí C ++ 17 implementované kompilátorem MSVC. Tato možnost zakáže kompilátoru a standardní knihovny podpora pro funkce, které se mění nebo nového ve verzích konceptu práce a defect aktualizace standardu jazyka C++ za C ++ 17.

**/Std: c ++ nejnovější** možnost povolí příspěvku-C ++ 17 funkcí jazyka a knihovny aktuálně implementováno v kompilátoru a knihovny. To může zahrnovat funkce z C ++ 20 práce koncept a defect aktualizace standardu C++, které nejsou zahrnuty v C ++ 17, jakož i experimentální návrhy koncept standardu. Seznam podporovaného jazyka a funkce knihovny najdete v tématu [co je nového v jazyce Visual c++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). **/Std: c ++ nejnovější** možnost nepovolíte funkce strážený **/ experimentální** přepínač, ale může být nutné je povolit.

> [!IMPORTANT]
> Kompilátor a knihovny Funkce povolené **/std: c ++ nejnovější** jsou k dispozici jako-je a bez podpory. Jsou v souladu s nebo bez předchozího upozornění. Jsou určeny jako verze preview funkcí jazyka, které se mohou objevit v příští verzi standard, ale standardní je ve vývoji. Použít **/std: c ++ 17** chcete používat funkce v nejnovější standardu ISO C++.

**/Std** možnost platit během kompilace jazyka C++ lze zjistit pomocí [ \_MSVC\_LANG](../../preprocessor/predefined-macros.md) makro preprocesoru. Další informace najdete v tématu [makra preprocesoru](../../preprocessor/predefined-macros.md).

**/Std: c ++ 14** a **/std: c ++ nejnovější** možnosti jsou k dispozici od verze Visual C++ 2015 Update 3. **/Std: c ++ 17** možnost je k dispozici od verze Visual C++ 2017 verze 15.3. Jak bylo uvedeno výše, některé standardu C ++ 17 chování zajišťuje **/std: c ++ 14** umožněné možnost, ale všechny ostatní funkce C ++ 17 **/std: c ++ 17**.

> [!NOTE]
> V závislosti na MSVC verze nebo aktualizace úroveň kompilátoru, nemusí plně implementovány některé funkce C ++ 14 a C ++ 17 nebo plně při zadávání splňující podmínky **/std: c ++ 14** nebo **/std: c ++ 17** možnosti. Například kompilátor Visual C++ 2017 RTM plně nepodporuje C ++ 14 podmínky shody `constexpr`, výraz SFINAE nebo vyhledávání názvů fázi 2. Přehled přizpůsobení jazyka C++ v jazyce Visual C++ ve verzi, naleznete v tématu [shoda jazyka Visual C++](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace**, **C/C++**, **jazyka**.

1. V **Standard jazyka C++**, vyberte standard jazyka podporují z ovládacího prvku rozevíracího seznamu a pak zvolte **OK** nebo **použít** uložte provedené změny.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
