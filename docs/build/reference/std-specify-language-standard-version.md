---
title: "-std (zadat standardní jazyková verze) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
dev_langs:
- C++
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb248f4c7ce1d9520bc328ed59b75ff081659996
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="std-specify-language-standard-version"></a>/STD (zadat jazykovou verzi standardní)

Povolit podporovány funkcí jazyka C++ z zadaná verze jazyka C++ standardní.

## <a name="syntax"></a>Syntaxe

> /std: [c ++ 14 | c ++ 17 | nejnovější c ++]

## <a name="remarks"></a>Poznámky

**/Std** možnost se používá k řízení C++ ISO specifické pro verzi, programovací jazyk standardní funkce povolené během kompilace kódu. Tato možnost umožňuje zakázat podporu pro určité nové funkce jazyka a knihovny, které je možné ukončit váš stávající kód, který odpovídá konkrétní verzi jazyka standardní. Ve výchozím nastavení **/std: c ++ 14** není zadaný, která zakáže jazyk a najít v novějších verzích jazyka C++ standardní funkce standardní knihovny. Použití **/std: c ++ 17** povolení funkce C ++ 17 specifické pro standardní a chování. Pokud chcete povolit explicitně nejnovější podporovanou kompilátoru a funkce standardní knihovny, použijte **/std: c ++ nejnovější**.

Výchozí hodnota **/std: c ++ 14** možnost umožňuje sadu funkce C ++ 14 implementované – kompilátor Visual C++. Tato možnost zakáže kompilátoru a standardní knihovny podpora pro funkce, které se změnily nebo nového v nejnovější verzi jazyka standardní, s výjimkou některé funkce C ++ 17 už implementované v předchozích verzích – kompilátor Visual C++. Aby se zabránilo nejnovější změny pro uživatele, kteří už udělali závislosti na funkcích, které jsou k dispozici od verze Visual Studio 2015 Update 2, tyto funkce zůstat zapnuté, kdy **/std: c ++ 14** je zadána možnost:

- [Pravidla pro automatické s braced seznamy init](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [TypeName v šabloně parametry šablony](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Odebrání trigraph](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atributy pro obory názvů a výčty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [U8 znakové literály](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Další informace na C ++ 14 a C ++ 17 funkce, které jsou povolené když **/std: c ++ 14** je zadán, najdete v poznámkách k v [přizpůsobení jazyka Visual C++](../../visual-cpp-language-conformance.md).
  
**/Std: c ++ 17** možnost umožňuje kompletní funkce C ++ 17 implementované – kompilátor Visual C++. Tato možnost zakáže kompilátoru a standardní knihovny podpora pro funkce, které se změnily nebo nové verze aktualizací práce koncept a vadou standardní C++ po C ++ 17.  
  
**/Std: c ++ nejnovější** možnost umožňuje sadu funkcí knihovna a jazyk C++ implementováno modulem Visual C++ pro sledování nejvíce poslední C ++ 20 práce koncept a vadou aktualizace standardní C++ které nejsou součástí C ++ 17. Pomocí tohoto přepínače lze získat v příspěvku – funkce C ++ 17 jazyk podporuje standardní knihovna a kompilátor. Seznam podporovaných jazyka a funkce knihovny najdete v tématu [co je nového pro Visual C++](../../what-s-new-for-visual-cpp-in-visual-studio.md). **/Std: c ++ nejnovější** možnost neumožňuje funkce budou dát **/ experimentální** přepínače.  
  
**/Std** možnost platit během kompilace C++ lze zjistit pomocí [ \_MSVC\_jazyk](../../preprocessor/predefined-macros.md) makro preprocesoru. Další informace najdete v tématu [preprocesor makra](../../preprocessor/predefined-macros.md).

**/Std: c ++ 14** a **/std: c ++ nejnovější** možnosti jsou dostupné od verze Visual C++ 2015 Update 3. **/Std: c ++ 17** možnost je k dispozici počínaje 2017 Visual C++ verze 15.3. Jak jsme uvedli výše, některé standardu C ++ 17 povoleno chování pomocí **/std: c ++ 14** možnost, ale všechny ostatní funkce C ++ 17 jsou povolené podle **/std: c ++ 17**.
  
> [!NOTE]
> V závislosti na Visual C++ verze nebo aktualizace úroveň kompilátoru, nemusí plně implementovat určité funkce C ++ 14 nebo C ++ 17 nebo plně vyhovující, když zadáte **/std: c ++ 14** nebo **/std: c ++ 17** možnosti. Například kompilátor Visual C++ 2017 RTM plně nepodporuje C ++ 14vyhovující `constexpr`, výraz sfinae u výrazů nebo vyhledání názvu fáze 2. Přehled přizpůsobení jazyka C++ v jazyce Visual C++ ve verzi najdete v tématu [přizpůsobení jazyka Visual C++](../../visual-cpp-language-conformance.md). 
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **C/C++**, **jazyk**.  
  
3.  V **standardní jazyk C++**, vyberte standardní jazykové podpory z ovládacího prvku rozevíracího seznamu a pak zvolte **OK** nebo **použít** uložte provedené změny.  
  
## <a name="see-also"></a>Viz také  
  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
