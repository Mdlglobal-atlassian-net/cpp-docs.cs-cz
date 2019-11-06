---
title: /STD (určení jazykové verze Standard)
ms.date: 05/16/2019
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 4583bef3ef3033b6ba493ccac1c4fc5360c70e35
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624893"
---
# <a name="std-specify-language-standard-version"></a>/STD (určení jazykové verze Standard)

Povolí podporované C++ funkce jazyka ze zadané verze C++ jazyka Standard.

## <a name="syntax"></a>Syntaxe

> /std:\[c++ 14\|c++ 17\|c + + nejnovější]

## <a name="remarks"></a>Poznámky

Možnost **/STD** je k dispozici v aplikaci Visual Studio 2017 nebo novější. Slouží k řízení standardních funkcí jazyka ISO C++ pro konkrétní verze, které jsou povoleny během kompilování kódu. Tato možnost umožňuje zakázat podporu některých nových funkcí jazyka a knihovny, které mohou poškodit stávající kód, který odpovídá určité verzi jazyka Standard. Ve výchozím nastavení je **/std: c++ 14** , což zakáže funkce jazyka a standardní knihovny, které se C++ nacházejí v novějších verzích jazyka Standard. Pomocí **/std: c++ 17** můžete povolit funkce a chování specifické pro c++ 17. Chcete-li explicitně povolit aktuálně implementované funkce kompilátoru a standardní knihovny, které jsou navrženy pro další koncept Standard, použijte **/std: c + + nejnovější**. Všechny funkce C++ 20 vyžadují **/std: C + + nejnovější**; Po dokončení implementace bude povolen nový **/std: možnost c++ 20** .

Výchozí **/std: možnost c++ 14** umožňuje sadu funkcí c++ 14 implementovaných kompilátorem MSVC. Tato možnost zakáže podporu kompilátoru a standardní knihovny pro funkce, které jsou změněny nebo novinkou v novějších verzích jazyka Standard, s výjimkou některých funkcí C++ 17, které jsou již implementovány v předchozích verzích kompilátoru MSVC. Aby nedocházelo k zásadním změnám pro uživatele, kteří již převzali závislosti na funkcích dostupných v rámci sady Visual Studio 2015 Update 2, zůstávají tyto funkce povoleny, pokud je zadána možnost **/std: c++ 14** :

- [Pravidla pro auto se systémem-init-seznamy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [TypeName v šabloně šablony – parametry](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Odebírá se trigraphs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atributy pro obory názvů a enumerátory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [U8 – znakové literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Další informace o tom, které funkce C++ 14 a C++ 17 jsou povolené při zadání **/std: c++ 14** , najdete v poznámkách v [tabulce pro shodu jazyků Microsoftu C++ ](../../overview/visual-cpp-language-conformance.md).

Možnost **/std: c++ 17** umožňuje úplnou sadu funkcí c++ 17 implementovaných kompilátorem MSVC. Tato možnost zakáže podporu kompilátoru a standardní knihovny pro funkce, které jsou změněny nebo novinkou ve verzích pracovního konceptu a aktualizacích chyb C++ Standard po c++ 17.

Možnost **/std: c + + nejnovější** umožňuje, aby byly v kompilátoru a knihovnách aktuálně implementovány funkce jazyka post-c + + 17 a knihovny. Ty můžou zahrnovat funkce z pracovního konceptu C++ 20 a aktualizace chyb C++ standardu, které nejsou zahrnuté do c++ 17, jakož i experimentální návrhy pro koncept Standard. Seznam podporovaných funkcí jazyka a knihovny najdete v tématu [co je nového pro vizuál C++ ](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). Možnost **/std: c + + nejnovější** nepovoluje funkce chráněné přepínačem **/Experimental** , ale může být vyžadováno jejich povolení.

> [!IMPORTANT]
> Funkce kompilátoru a knihovny, které jsou povolené funkcí **/std: c + +** , představují funkce, které se mohou C++ objevit v budoucím standardu a také funkce c++ 20, které jsou schváleny. Funkce, které nebyly schváleny, se vztahují k zásadním změnám nebo odebrání bez předchozího upozornění a jsou poskytovány na základě. 

Možnost **/STD** v účinnosti během C++ kompilace lze zjistit pomocí makra preprocesor preprocesoru [\_jazyka\_MSVC](../../preprocessor/predefined-macros.md) . Další informace naleznete v tématu [makra preprocesoru](../../preprocessor/predefined-macros.md).

**/Std: c++ 14** a **/std: nejnovější možnosti c + +** jsou k dispozici počínaje verzí Visual Studio 2015 Update 3. Možnost **/std: c++ 17** je k dispozici počínaje verzí Visual Studio 2017 verze 15,3. Jak bylo uvedeno výše, některé standardní chování C++ 17 je povoleno pomocí možnosti **/std: c++ 14** , ale všechny ostatní funkce c++ 17 jsou povoleny v **/std: c++ 17**. Funkce c++ 20 jsou povoleny funkcí **/std: nejnovější** , dokud nebude implementace dokončena.

> [!NOTE]
> V závislosti na verzi kompilátoru MSVC nebo na úrovni aktualizace nemusí být funkce C++ 17 plně implementované nebo plně vyhovující, když zadáte **/std: možnosti c++ 17** . Přehled souladu C++ jazyka ve vizuálu C++ podle verze Release najdete v tématu Tabulka pro [shodu jazyka C++ Microsoft](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace**, jazyk **CC++/** , **jazyk**.

1. V  **C++ části Language standard**zvolte Standard jazyka pro podporu z ovládacího prvku DropDown a pak zvolte **OK** nebo **použít** pro uložení změn.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
