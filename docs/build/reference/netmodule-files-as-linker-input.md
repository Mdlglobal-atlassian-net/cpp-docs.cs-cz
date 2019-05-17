---
title: Soubory .netmodule jako vstup linkeru
ms.date: 05/16/2019
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: 50a0f0a1ff5f65a7512e8372de2fe5296c866dca
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837429"
---
# <a name="netmodule-files-as-linker-input"></a>Soubory .netmodule jako vstup linkeru

Link.exe přijímá jako vstup nyní .obj jazyka MSIL a modulů .NET. Výstupní soubor vytvořený pomocí linkeru je sestavení nebo modul .NET se bez závislostí za běhu na žádném z .obj nebo modulů .NET, které byly vstup do linkeru.

modulů .NET vytvářejí a kompilátorem MSVC s [/LN (vytvoření modulu MSIL)](ln-create-msil-module.md) nebo pomocí linkeru spuštěného s [parametr/noassembly (vytvoření modulu MSIL)](noassembly-create-a-msil-module.md). .objs se vždy vytvářejí ve kompilace jazyka Visual C++. U dalších kompilátorů aplikace Visual Studio, použijte **/target: Module** – možnost kompilátoru.

Je nutné předat do linkeru soubor .obj z kompilace jazyka Visual C++, který vytvořili .netmodule. Předávání .netmodule se už nepodporuje, protože **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v sadě Visual Studio 2017 a novější.

Informace o tom, jak vyvolání linkeru z příkazového řádku najdete v tématu [syntaxe příkazového řádku Linkeru](linking.md), [použít MSVC nástrojů z příkazového řádku](../building-on-the-command-line.md), a [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Předání soubor .netmodule nebo DLL linkeru, který byl zkompilován kompilátorem MSVC s **/CLR** může vést k chybě propojovacího programu. Další informace najdete v tématu [výběr formátu vstupních souborů .netmodule](choosing-the-format-of-netmodule-input-files.md).

Linker přijímá nativní .obj soubory, jakož i soubory .obj jazyka MSIL zkompilována pomocí **/CLR**. Při předávání smíšených .objs ve stejném sestavení, je ověřitelnost výsledného výstupního souboru, ve výchozím nastavení, bude rovna nejnižší úrovni ověřitelnosti výstupních modulů.

Pokud aktuálně máte aplikaci, která se skládá ze dvou nebo více sestavení a chcete, aby aplikace, které mají být obsažena v jednom sestavení, musíte znovu zkompilovat sestavení a potom propojte .objs nebo modulů .NET pro tvoří jedno sestavení.

Je nutné zadat vstupní bod pomocí [/Entry (Symbol vstupního bodu)](entry-entry-point-symbol.md) při vytváření spustitelné bitové kopie.

Při propojování s soubor .obj nebo modul .NET MSIL, použijte [parametru/LTCG (generování kódu při propojování odkaz)](ltcg-link-time-code-generation.md), v opačném případě pokud linker zjistí .obj jazyka MSIL nebo modul .NET, se restartuje propojení pomocí parametru/LTCG.

Soubory .obj nebo modul .NET MSIL může také předaných do cl.exe.

Vstupní soubory .obj nebo modul .NET MSIL, nemůže mít vložené prostředky. Prostředek je vložen do výstupního souboru (modulu nebo sestavení) s [narozdíl od (vložení spravovaného prostředku)](assemblyresource-embed-a-managed-resource.md) – možnost linkeru nebo se **/Resource** – možnost kompilátoru v dalších kompilátorů aplikace Visual Studio.

Při provádění MSIL propojování a také nezadáte [parametru/LTCG (generování kódu při propojování odkaz)](ltcg-link-time-code-generation.md), zobrazí se informační zpráva oznámení, že propojení se restartuje. Tuto zprávu můžete ignorovat, ale chcete-li zlepšit výkon linkeru s propojení jazyka MSIL, explicitně určete **parametru/LTCG**.

## <a name="example"></a>Příklad

V kódu jazyka C++ **catch** blok odpovídající **zkuste** bude vyvolána výjimka Nesystémová. Ale ve výchozím nastavení, modul CLR zabalí nesystémové výjimek pomocí <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Když se vytvoří sestavení z modulů Visual C++ a jiné než Visual C++ a chcete, aby **catch** blokovat v kódu jazyka C++, které mají být vyvolány z odpovídající **zkuste** klauzule při **zkuste**nesystémové bloku výjimku, je nutné přidat `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` atribut ke zdrojovému kódu pro moduly než C++.

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

Změnou logickou hodnotu `WrapNonExceptionThrows` atributů, změníte schopnost kód jazyka Visual C++ – Nesystémová výjimku zachytit.

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

- [Vstupní soubory LINK](link-input-files.md)
- [Možnosti linkeru MSVC](linker-options.md)
