---
title: /H (Omezit délku externích názvů)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: 194f8d2c87eb6aa307f417ff022e7975edf2ccc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489827"
---
# <a name="h-restrict-length-of-external-names"></a>/H (Omezit délku externích názvů)

Zastaralé Omezí délku externích názvů.

## <a name="syntax"></a>Syntaxe

> **/H**<em>číslo</em>

## <a name="arguments"></a>Arguments

*Číslo*<br/>
Určuje maximální délku externích názvů povolené v programu.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je délku externích (veřejných) názvů 2 047 znaků. To platí pro programy C a C++. Pomocí **/H** může pouze snížit maximální povolenou délku identifikátory, neukončil jej. Mezera mezi **/H** a *číslo* je volitelný.

Pokud program obsahuje externí názvy delší než *číslo*, jsou přesahující znaky ignorovány. Pokud kompilujete aplikace bez **/H** a pokud identifikátoru obsahuje více než 2 047 znaky, bude kompilátor generovat [závažná chyba C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

Omezení na délku zahrnuje všechny kompilátor vytvoří počáteční podtržítko (**\_**) nebo zavináč (**\@**). Tyto znaky jsou součástí identifikátoru a využijte významné umístění.

- Kompilátor přidá vedoucího podtržítka (**\_**) k názvům změnil `__cdecl` (výchozí) a `__stdcall` konvence volání a jeden z předních zavináč (**\@** ) k názvům změnil `__fastcall` konvence volání.

- Kompilátor připojí informací o argumentech velikosti na názvy upravil `__fastcall` a `__stdcall` konvence volání a přidá informace o typu pro názvy v jazyce C++.

Může být pro vás **/H** užitečné:

- Při vytváření programů jazyků nebo přenosné.

- Při použití nástroje, které se uplatňují omezení délky externích identifikátorů.

- Pokud chcete omezit množství místa, použijte symboly v sestavení pro ladění.

Následující příklad ukazuje způsob použití **/H** může ve skutečnosti způsobit chyby, pokud identifikátor délky jsou omezené příliš mnoho:

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

Musíte také být opatrní při použití **/H** možnost z důvodu identifikátory předdefinovaných kompilátoru. Pokud identifikátor maximální délka je příliš malá, budou některé předdefinované identifikátory nevyřešené také určité knihovna volání funkcí. Například pokud `printf` funkce se používá a možnost **/H5** určena v době kompilace, symbol **_prin** bude vytvořen, aby bylo možné odkazovat `printf`, a to nebude nalezena v knihovně.

Použití **/H** není kompatibilní s [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).

**/H** od verze Visual Studio 2005 je zastaralá možnost; zvýšily se limity maximální délku a **/H** už nepotřebujete. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadáním možnosti kompilátoru v **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
