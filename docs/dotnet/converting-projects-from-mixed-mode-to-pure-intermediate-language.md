---
title: Převod projektů ze smíšeného režimu do čistého IL (Intermediate Language)
ms.date: 11/04/2016
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 2f63b6860157e315d44f7c050812a7f0b97f2726
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448051"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Převod projektů ze smíšeného režimu do čistého IL

Všechny projekty Visual C++ CLR se propojit ke knihovnám C za běhu ve výchozím nastavení. V důsledku toho tyto projekty jsou klasifikovány jako aplikací ve smíšeném režimu, protože jejich kombinací nativního kódu s kódem, který se zaměřuje na modul CLR (spravovaný kód). Když jsou zkompilovány, jsou zkompilovány do (IL intermediate language), říká také jazyk Microsoft intermediate language (MSIL).

> [!IMPORTANT]
> Zastaralé Visual Studio 2015 a Visual Studio 2017 už nepodporuje vytváření **/CLR: pure** nebo **/CLR: safe** kódu pro aplikace modulu CLR. Pokud budete potřebovat pure nebo bezpečné sestavení, doporučujeme že převést aplikaci do jazyka C#.

Pokud používáte starší verzi sady Microsoft C++ sada nástrojů kompilátoru, který podporuje **/CLR: pure** nebo **/CLR: safe**, tento postup slouží k převodu kódu do prázdné MSIL:

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Chcete-li převést aplikace ve smíšeném režimu do čistého IL

1. Odebrat odkazy na [běhových knihoven C](../c-runtime-library/crt-library-features.md) (CRT):

   1. Soubor .cpp definuje vstupní bod aplikace, změňte vstupní bod do `Main()`. Pomocí `Main()` označuje, že váš projekt neobsahuje odkazy na CRT.

   2. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **vlastnosti** v místní nabídce pro otevření stránek vlastností pro vaši aplikaci.

   3. V **Upřesnit** stránku vlastností projektu **Linkeru**, vyberte **vstupní bod** a pak zadejte **hlavní** do tohoto pole.

   4. Pro konzolové aplikace v **systému** stránku vlastností projektu **Linkeru**, vyberte **subsystému** pole a změnit tuto hodnotu na **konzoly (/ Subsystem:Console)**.

      > [!NOTE]
      > Není nutné nastavit tuto vlastnost pro aplikace Windows Forms, protože **subsystému** je nastaveno na **Windows (/ SUBSYSTEM: WINDOWS)** ve výchozím nastavení.

   5. Ve stdafx.h okomentujte všechny `#include` příkazy. Například v konzolové aplikace:

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       -nebo-

       Například v aplikacích Windows Forms:

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. Pro aplikace Windows Forms v souboru Form1.CPP příkaz zakomentujte `#include` příkaz, který odkazuje na windows.h. Příklad:

      ```cpp
      // #include <windows.h>
      ```

2. Stdafx.h přidejte následující kód:

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Odeberte všechny nespravované typy:

   Bez ohledu na to vhodné, nahradit odkazy na struktury z nespravovaného typy [systému](/dotnet/api/system) oboru názvů. V následující tabulce jsou uvedeny běžné spravované typy:

   |Struktura|Popis|
   |---------------|-----------------|
   |[Datový typ Boolean](/dotnet/api/system.boolean)|Představuje logickou hodnotu.|
   |[Bajtů](/dotnet/api/system.byte)|Představuje celé číslo bez znaménka 8 bitů.|
   |[Char](/dotnet/api/system.char)|Hodnota představuje znak Unicode.|
   |[Datum a čas](/dotnet/api/system.datetime)|Představuje okamžik v čase, obvykle vyjádřený jako datum a čas.|
   |[Decimal](/dotnet/api/system.decimal)|Představuje desetinné číslo.|
   |[Double](/dotnet/api/system.double)|Představuje číslo s plovoucí desetinnou čárkou dvojitou přesností.|
   |[identifikátor GUID](/dotnet/api/system.guid)|Představuje globálně jedinečný identifikátor (GUID).|
   |[Int16](/dotnet/api/system.int16)|Představuje 16bitové celé číslo se znaménkem.|
   |[Int32](/dotnet/api/system.int32)|Představuje 32bitové celé číslo se znaménkem.|
   |[Int64](/dotnet/api/system.int64)|Představuje 64bitové celé číslo se znaménkem.|
   |[IntPtr](/dotnet/api/system.intptr)|Typ specifické pro platformu, která se používá k reprezentaci ukazatele nebo popisovače.|
   |[SByte –](/dotnet/api/system.byte)|Představuje 8bitové celé číslo se znaménkem.|
   |[Jeden](/dotnet/api/system.single)|Představuje číslo s plovoucí desetinnou čárkou jednoduchou přesností.|
   |[TimeSpan](/dotnet/api/system.timespan)|Představuje časový interval.|
   |[UInt16](/dotnet/api/system.uint16)|Představuje celé číslo bez znaménka 16 bitů.|
   |[UInt32](/dotnet/api/system.uint32)|Představuje celé číslo bez znaménka 32-bit.|
   |[UInt64](/dotnet/api/system.uint64)|Představuje celé číslo bez znaménka 64-bit.|
   |[UIntPtr](/dotnet/api/system.uintptr)|Typ specifické pro platformu, která se používá k reprezentaci ukazatele nebo popisovače.|
   |[Typ void](/dotnet/api/system.void)|Označuje metodu, která nevrací hodnotu; To znamená že metoda nemá návratový typ void.|