---
title: soubory .netmodule jako vstup Linkeru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb2ab74e8c9d0285b9bec2f9979257d89797022
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704562"
---
# <a name="netmodule-files-as-linker-input"></a>Soubory .netmodule jako vstup linkeru

Link.exe nyní přijme MSIL .obj a .netmodules jako vstup. Výstupní soubor vyprodukované linkeru je sestavení nebo .netmodule s žádné běhu závislost na .obj nebo .netmodules, že se vstupní linkeru.

.netmodules jsou vytvořené pomocí – kompilátor Visual C++ s [/LN (vytvořit modul MSIL)](../../build/reference/ln-create-msil-module.md) nebo linkeru s [/NOASSEMBLY (vytvořit modul MSIL)](../../build/reference/noassembly-create-a-msil-module.md). .objs se vytváří vždy v kompilaci Visual C++. Pro ostatní kompilátory Visual Studio, použijte **/target: Module** – možnost kompilátoru.

Je nutné předat do linkeru souboru .obj z kompilace Visual C++, který vytvořili .netmodule. Předávání .netmodule se už nepodporuje, protože **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Informace o tom, jak vyvolání linkeru z příkazového řádku najdete v tématu [syntaxe příkazového řádku Linkeru](../../build/reference/linker-command-line-syntax.md), [kódu sestavení C/C++ v příkazovém řádku](../../build/building-on-the-command-line.md), a [nastavení cesty a proměnných prostředí pro Sestavení příkazového řádku](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

Předávání soubor .netmodule nebo .dll linkeru se zkompilují – kompilátor Visual C++ s **/CLR** může způsobit chybu linkeru. Další informace najdete v tématu [Volba formátu .netmodule vstupních souborů](../../build/reference/choosing-the-format-of-netmodule-input-files.md).

Linkeru přijímá soubory .obj nativní, jakož i soubory .obj MSIL kompilovat s **/CLR**. Při předávání smíšený .objs ve stejném sestavení, ověřitelnosti výsledné výstupního souboru, ve výchozím nastavení, bude rovnat nejnižší úroveň ověřitelnosti vstupní modulů.

Pokud aktuálně máte aplikaci, která se skládá ze dvou nebo více sestavení a chcete, aby aplikace, které mají být obsažena v jednom sestavení, musíte znovu zkompiluje sestavení a potom na odkaz .objs nebo .netmodules k vytvoření jednoho sestavení.

Musíte zadat bod položka pomocí [/Entry (Symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md) při vytváření spustitelné bitové kopie.

Při propojení s souboru .obj nebo .netmodule MSIL, použijte [/ltgc (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md), jinak při linkeru zaznamená MSIL .obj nebo .netmodule, ho restartuje odkaz s/ltgc.

Soubory .obj nebo .netmodule MSIL může být předán cl.exe.

Vstupní soubory .obj nebo .netmodule MSIL nelze vložené prostředky. Prostředek je vložen do výstupního souboru (modulu nebo sestavení) s [/ASSEMBLYRESOURCE (vložení spravované prostředků)](../../build/reference/assemblyresource-embed-a-managed-resource.md) – možnost linkeru nebo s **/Resource** – možnost kompilátoru v jiných kompilátory Visual Studio.

Při provádění MSIL propojování a také nezadáte [/ltgc (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md), zobrazí se informační zpráva vytváření sestav, že je odkaz restartování. Tuto zprávu můžete ignorovat, ale chcete-li zlepšit výkon linkeru s MSIL propojování, explicitně zadáte **/ltgc**.

## <a name="example"></a>Příklad

V kódu C++ **catch** blok odpovídající **zkuste** bude volána pro nesystémové výjimku. Nicméně ve výchozím modulu CLR zabalí nesystémové výjimky s <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Při sestavení je vytvořený z modulů Visual C++ a mimo jazyk Visual C++ a chcete **catch** blokovat v kódu C++ má být volána z jeho odpovídající **zkuste** klauzule při **zkuste**bloku vyhodí výjimku nesystémové, je nutné přidat `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` atribut zdrojový kód pro jiný C++ moduly.

```cpp
// MSIL_linking.cpp
// compile with: /c /clr
value struct V {};

ref struct MCPP {
   static void Test() {
      try {
         throw (gcnew V);
      }
      catch (V ^) {
         System::Console::WriteLine("caught non System exception in C++ source code file");
      }
   }
};

/*
int main() {
   MCPP::Test();
}
*/
```

## <a name="example"></a>Příklad

Změnou logickou hodnotu `WrapNonExceptionThrows` atribut upravit kód jazyka Visual C++ schopnost zachycení nesystémové výjimky.

```cpp
// MSIL_linking_2.cs
// compile with: /target:module /addmodule:MSIL_linking.obj
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console
using System.Runtime.CompilerServices;

// enable non System exceptions
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]

class MLinkTest {
   public static void Main() {
      try {
         MCPP.Test();
      }
      catch (RuntimeWrappedException) {
         System.Console.WriteLine("caught a wrapped exception in C#");
      }
   }
}
```

```Output
caught non System exception in C++ source code file
```

## <a name="see-also"></a>Viz také:

- [Vstupní soubory LINK](../../build/reference/link-input-files.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
