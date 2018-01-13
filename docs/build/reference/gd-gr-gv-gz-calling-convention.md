---
title: "-Gd, / - Gr, - Gv, - Gz (konvence volání) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
dev_langs: C++
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26e88abf30c0f67fe5b104d560c40dd2adc57752
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konvence volání)
Tyto možnosti můžete určit pořadí, ve které funkci argumenty jsou vloženy do zásobníku, zda volající funkce nebo volaná funkce odebere argumenty v zásobníku volání na konci a konvence architekturu název, který kompilátor používá k identifikaci jednotlivé funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Gd  
/Gr  
/Gv  
/Gz  
```  
  
## <a name="remarks"></a>Poznámky  
 **/GD**, výchozí nastavení, určuje [__cdecl](../../cpp/cdecl.md) konvence volání u všech funkcí kromě C++ členských funkcí a funkcí, které jsou označené [__stdcall](../../cpp/stdcall.md), [__ fastcall](../../cpp/fastcall.md), nebo [__vectorcall](../../cpp/vectorcall.md).  
  
 **GR** Určuje `__fastcall` konvence volání u všech funkcí kromě C++ členské funkce, funkce s názvem `main`a funkce, které jsou označeny `__cdecl`, `__stdcall`, nebo `__vectorcall`. Všechny `__fastcall` funkce musí mít prototypy. Tato konvence volání je dostupný jenom v kompilátory, které cílí x86 a je ignorován v kompilátory, které cílí jiné architektury.  
  
 **/GZ** Určuje `__stdcall` konvence volání u všech funkcí kromě C++ členské funkce, funkce s názvem `main`a funkce, které jsou označeny `__cdecl`, `__fastcall`, nebo `__vectorcall`. Všechny `__stdcall` funkce musí mít prototypy. Tato konvence volání je dostupný jenom v kompilátory, které cílí x86 a je ignorován v kompilátory, které cílí jiné architektury.  
  
 **/ Gv** Určuje `__vectorcall` konvence volání u všech funkcí kromě C++ členské funkce, funkce s názvem hlavní, funguje s `vararg` seznam argumentů s proměnnou nebo funkce, které jsou označené konfliktní `__cdecl`, `__stdcall`, nebo `__fastcall` atribut. Tato konvence volání je k dispozici pouze na x86 a x64 architektury, které podporují /arch:SSE2 a vyšší a je ignorován v kompilátory, které cílí architekturu ARM.  
  
 Funkcí, které přijímají proměnný počet argumentů musí být označen `__cdecl`.  
  
 **/GD**, **GR**, **/gv** a **/Gz** nejsou kompatibilní s [/CLR: safe](../../build/reference/clr-common-language-runtime-compilation.md) nebo   **/CLR: pure**. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
> [!NOTE]
>  Ve výchozím nastavení pro x86 procesory, C++ členské funkce používají [__thiscall](../../cpp/thiscall.md).  
  
 Pro všechny procesory, členské funkce, který je explicitně označen jako `__cdecl`, `__fastcall`, `__vectorcall`, nebo `__stdcall` používá zadaná konvence volání, pokud není na této architektuře ignorována. Členské funkce, která přebírá proměnný počet argumentů vždy používá `__cdecl` konvence volání.  
  
 Tyto možnosti kompilátoru mít žádný vliv na dekorování názvů C++ metod a funkce. Pokud není deklarován jako `extern "C"`, metody C++ a funkce použít jiné schéma architekturu název. Další informace najdete v tématu [dekorované názvy](../../build/reference/decorated-names.md).  
  
 Další informace o volání konvencí najdete v tématu [konvence volání](../../cpp/calling-conventions.md).  
  
## <a name="cdecl-specifics"></a>__cdecl podrobností  
 Na x86 procesory. všechny argumenty funkce se předávají v zásobníku zprava doleva. Na ARM a x64 architektury, některé argumenty nejsou předávány registrace a zbývající se předávají v zásobníku zprava doleva. Volání rutiny POP argumenty v zásobníku.  
  
 Pro jazyk C `__cdecl` naming convention používá název funkce před sebou podtržítko ( `_` ); není proveden žádný případu překlad. Pokud není deklarován jako `extern "C"`, funkcí jazyka C++ pomocí jiné schéma architekturu název. Další informace najdete v tématu [dekorované názvy](../../build/reference/decorated-names.md).  
  
## <a name="fastcall-specifics"></a>__fastcall podrobností  
 Některé `__fastcall` argumenty funkce jsou předány v registrech (pro x86 procesory, ECX a EDX), a zbývající jsou vloženy do zásobníku zprava doleva. Vyvolání rutiny se zobrazí tyto argumenty v zásobníku, než vrátí. Obvykle **GR** zkracuje dobu provádění.  
  
> [!NOTE]
>  Buďte opatrní při použití `__fastcall` konvence volání pro všechny funkce, která je napsán v jazyce vloženého sestavení. Používání registrů mohla být v konfliktu s použitím kompilátoru.  
  
 Pro jazyk C `__fastcall` naming convention používá název funkce před sebou znaku zavináče (`@`) a velikost argumenty v bajtech. Je potřeba žádné případu překlad. Kompilátor používá tuto šablonu pro vytváření názvů:  
  
```  
@function_name@number  
```  
  
 Při použití `__fastcall` zásady vytváření názvů, používat standardní zahrnout soubory. Jinak zobrazí se nerozpoznané externí odkazy.  
  
## <a name="stdcall-specifics"></a>__stdcall podrobností  
 A `__stdcall` argumenty funkce jsou vloženy do zásobníku zprava doleva a volaná funkce POP tyto argumenty v zásobníku před vrátí.  
  
 Pro jazyk C `__stdcall` naming convention používá název funkce před sebou podtržítko ( `_` ), za kterými by znaku zavináče (@) a velikost argumenty v bajtech. Není proveden žádný případu překlad. Kompilátor používá tuto šablonu pro vytváření názvů:  
  
```  
_functionname@number  
```  
  
## <a name="vectorcall-specifics"></a>specifika __vectorcall  
 A `__vectorcall` argumenty funkce celé číslo se předanou hodnotu, pomocí až dvě (na x86) nebo čtyři (v x64) celé číslo zaregistruje a až šest XMM zaregistruje pro s plovoucí desetinnou čárkou a vektoru hodnoty a zbytek se předávají v zásobníku zprava doleva. Volaná funkce vyčistí ze zásobníku před vrátí. Vektor a návratové hodnoty s plovoucí desetinnou čárkou jsou vráceny v XMM0.  
  
 Pro jazyk C `__vectorcall` zásady vytváření názvů používá název funkce, za nímž následuje dva znak @@ a velikost argumenty v bajtech. Není proveden žádný případu překlad. Kompilátor používá tuto šablonu pro vytváření názvů:  
  
```  
functionname@@number  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **Upřesnit** stránku vlastností.  
  
4.  Změnit **konvence volání** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)