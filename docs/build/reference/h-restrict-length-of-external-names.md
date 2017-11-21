---
title: "-H (omezit délku externích názvů) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /h
dev_langs: C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a69bf1b4e6b2e552bd73594a2c33f092570b94c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="h-restrict-length-of-external-names"></a>/H (Omezit délku externích názvů)
Zastaralé Omezuje délku externích názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Hnumber  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Určuje maximální délku externích názvů povolené v programu.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je délku externích (veřejných) názvů 2,047 znaků. To platí pro programy C a C++. Pomocí **/H** lze pouze snížit maximální povolenou délku identifikátorů, není zvýšit ji. Mezery mezi **/H** a `number` je volitelný.  
  
 Obsahuje-li program externí názvy delší než `number`, navíc znaky jsou ignorovány. Pokud je program bez **/H** a pokud identifikátor obsahuje více než 2,047 znaky, vygeneruje kompilátor [závažná chyba C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).  
  
 Limit délky zahrnuje všechny vytvořené kompilátoru úvodní podtržítka (_) nebo znaku zavináče (@). Tyto znaky jsou součástí identifikátor a proveďte významné umístění.  
  
-   Kompilátor přidá úvodní podtržítka (_) na názvy upraveném `__cdecl` (výchozí) a `__stdcall` konvence volání a jako úvodní znak (@) na názvy upraveném `__fastcall` konvence volání.  
  
-   Kompilátor připojí argument velikost informace názvy upraveném `__fastcall` a `__stdcall` konvence volání a přidá informace o typu názvy v jazyce C++.  
  
 Možná **/H** užitečné:  
  
-   Při vytváření smíšený jazyk nebo přenosné programy.  
  
-   Při použití nástroje, které uložit omezení na délce externí identifikátory.  
  
-   Pokud chcete omezit množství místa, které používají symboly v sestavení ladicí verze.  
  
 Následující příklad ukazuje způsob použití **/H** můžete ve skutečnosti znamenat chyby, pokud identifikátor délky jsou omezené příliš mnoho:  
  
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
  
 Také musí být opatrní při používání **/H** možnost kvůli identifikátory předdefinovaných kompilátoru. Pokud délka maximální identifikátor je příliš malá, bude určité předdefinované identifikátory volání funkcí knihovny nerozpoznané a také některé. Například pokud `printf` je použita funkce a možnost **/H5** je zadána při kompilaci, symbol **_prin** vytvoří odkázat `printf`, a to nebude nalezeno v knihovně.  
  
 Použití **/H** není kompatibilní s [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).  
  
 **/H** parametr se již nepoužívá, protože Visual Studio 2005; zvýšili omezení maximální délku a **/H** již není potřeba. Seznam – možnosti kompilátoru zastaralé, najdete v části **zastaralé a odebrat – možnosti kompilátoru** v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)