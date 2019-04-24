---
title: /Zc:sizedDealloc (povolení funkcí Dealokace v globálním)
ms.date: 03/06/2018
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
ms.openlocfilehash: dc381058c6a2ef84542be1d3cdd00c410aa51c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315479"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc:sizedDealloc (povolení funkcí Dealokace v globálním)

**/Zc:sizedDealloc** – možnost kompilátoru instruuje kompilátor, aby přednostně volání globální `operator delete` nebo `operator delete[]` funkcí, které mají druhý operátor typu `size_t` když je k dispozici velikost objektu. Tyto funkce může používat `size_t` parametr k optimalizaci výkonu dealokátor.

## <a name="syntax"></a>Syntaxe

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>Poznámky

V C ++ 11 standard, můžete definovat statické členské funkce `operator delete` a `operator delete[]` , které přebírají sekundy, `size_t` parametru. Obvykle se používá v kombinaci s [operátor new](../../cpp/new-operator-cpp.md) funkce implementovat efektivnější alokátorů a deallocators pro objekt. C ++ 11, ale nedefinovala ekvivalentní sadu funkcí dealokace v globálním oboru. V C ++ 11, globální funkce dealokace v, které mají druhý operátor typu `size_t` jsou považovány za funkce Odstranit umístění. Je nutné explicitně volat předáním velikost argumentu.

C ++ 14 standardní mění chování kompilátoru. Při definování globálních `operator delete` a `operator delete[]` , které přebírají druhý operátor typu `size_t`, kompilátor dává přednost volat tyto funkce, pokud nejsou vyvolány člen rozsah verzí a velikost objektu je k dispozici. Kompilátor implicitně předá velikost argumentu. Verze jediný argument se volá se, když kompilátor nemůže určit velikost objektu navrácena. V opačném případě obvyklých pravidel pro výběr verze funkce zrušení přidělení k vyvolání stále platí. Volání globálních funkcí může být explicitně určeno předřazení operátoru rozlišení oboru (`::`) k volání funkce zrušení přidělení.

Ve výchozím nastavení spouští se v sadě Visual Studio 2015 Visual C++ implementuje toto C ++ 14 standardní chování. Můžete to explicitně zadat tak, že nastavíte **/Zc:sizedDealloc** – možnost kompilátoru. Reprezentuje potenciálně zásadní změnu. Použít **/Zc:sizedDealloc-** možnost pro zachování původního chování, například když váš kód definuje operátory odstranit umístění, které použijte druhý operátor typu `size_t`. Výchozí implementace knihovny sady Visual Studio globální zrušení přidělení funkce, které mají druhý operátor typu `size_t` vyvolat verze jeden parametr. Pokud váš kód poskytuje pouze jedním parametrem globální operátor delete a operátor delete [], vyvolají výchozí implementace knihovny funkce globální velikostí dealokace globální funkce.

**/Zc:sizedDealloc** – možnost kompilátoru je ve výchozím. [/ Permissive-](permissive-standards-conformance.md) nemá vliv na možnost **/Zc:sizedDealloc**.

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Z **konfigurace** rozevírací nabídku, vyberte **všechny konfigurace**.

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc:sizedDealloc** nebo **/Zc:sizedDealloc-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (shoda)](zc-conformance.md)<br/>
