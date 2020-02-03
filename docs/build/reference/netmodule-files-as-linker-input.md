---
title: .netmodule soubory jako vstup linkeru
description: Popisuje, jak používat Mixed.obj ani.netmodule soubory jako vstup linkeru při vytváření sestavení .NET.
ms.date: 01/30/2020
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodule files
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
no-loc:
- obj
- netmodule
- clr
- pure
- safe
ms.openlocfilehash: 83eab25624bdb81ba9191e4efe6a774551502ee0
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912816"
---
# <a name="opno-locnetmodule-files-as-linker-input"></a>.netmodule soubory jako vstup linkeru

Link. exe přijímá *`.obj`* MSIL a *`.netmodule`* soubory jako vstup. Výstupní soubor vytvořený linkerem je sestavení nebo *`.netmodule`* soubor bez závislosti za běhu na žádném z *`.obj`* nebo *`.netmodule`* souborů, které byly zadány do linkeru.

## <a name="remarks"></a>Poznámky

*`.netmodule`* soubory jsou vytvářeny pomocí kompilátoru MSVC s [/ln (vytvořit modul MSIL)](ln-create-msil-module.md) nebo linkerem s [/NOASSEMBLY (vytvořit modul MSIL)](noassembly-create-a-msil-module.md). *`.obj`* soubory jsou vždy vytvářeny v C++ kompilaci. Pro ostatní kompilátory sady Visual Studio použijte možnost kompilátoru **/target: Module** .

Linker musí předat *`.obj`* soubor ze C++ kompilace, která vytvořila *`.netmodule`* . Předání do *`.netmodule`* již není podporováno, protože **/clr:pure** a/clr **:** možnosti kompilátorusafejsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017 a novější.

Informace o tom, jak volat linker z příkazového řádku, naleznete v tématu [syntaxe příkazového řádku linkeru](linking.md), [použití sady nástrojů MSVC z příkazového řádku](../building-on-the-command-line.md)a [Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Předání *`.netmodule`* nebo *`.dll`* souboru linkeru, který je zkompilován kompilátorem MSVC s **/clr** může mít za následek chybu linkeru. Další informace najdete v tématu [Volba formátu vstupních souborů .netmodule ](choosing-the-format-of-netmodule-input-files.md).

Linker přijímá jak nativní soubory *`.obj`* , tak soubory *`.obj`* jazyka MSIL zkompilované pomocí **/clr** . Můžete předat smíšené *`.obj`* soubory ve stejném sestavení. Výsledná výchozí ověřitel výstupního souboru je stejná jako u nejnižší ověřitelného vstupního modulu.

Můžete změnit aplikaci, která se skládá ze dvou nebo více sestavení, aby byla obsažena v jednom sestavení. Znovu zkompilujte zdroje sestavení a potom propojte soubory *`.obj`* nebo soubory *`.netmodule`* a vytvořte jedno sestavení.

Při vytváření spustitelné image určete vstupní bod s použitím [/entry (symbol vstupního bodu)](entry-entry-point-symbol.md) .

Při propojování s *`.obj`* nebo *`.netmodule`* souboru jazyka MSIL, použijte [/LTCG (generování kódu při propojování)](ltcg-link-time-code-generation.md), jinak, pokud linker zjistí *`.obj`* nebo *`.netmodule`* jazyka MSIL, restartuje propojení s **/LTCG**. Zobrazí se informační zpráva s informacemi o restartování tohoto odkazu. Tuto zprávu můžete ignorovat, ale chcete-li zlepšit výkon linkeru, explicitně zadejte **/LTCG**.

Do cl. exe lze také předat soubory MSIL *`.obj`* nebo *`.netmodule`* .

Vstupní prostředky MSIL *`.obj`* nebo *`.netmodule`* soubory nemůžou mít vložené prostředky. Vložení prostředků do výstupního modulu nebo souboru sestavení pomocí možnosti linkeru [/ASSEMBLYRESOURCE (vložení spravovaného prostředku)](assemblyresource-embed-a-managed-resource.md) Nebo použijte možnost kompilátoru **/Resource** v dalších kompilátorech sady Visual Studio.

## <a name="examples"></a>Příklady

V C++ kódu se pro výjimku bez`System` vyvolá **`catch`** blok odpovídající **`try`** . Ve výchozím nastavení však CLR balí výjimky, které nejsou`System`, s <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Když C++ je sestavení vytvořeno z aC++ nemoduly a chcete, aby byl **`catch`** blok v C++ kódu vyvolán z odpovídající klauzule **`try`** , když blok **`try`** vyvolá výjimku, která není`System`, je nutné přidat atribut `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` do zdrojového kódu pro jiné nežC++ moduly.

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

Změnou `Boolean` hodnoty atributu `WrapNonExceptionThrows` upravíte schopnost C++ kódu zachytit výjimku, která není`System`.

```csharp
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
