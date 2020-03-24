---
title: Převod projektů ze smíšeného režimu do čistého IL (Intermediate Language)
ms.date: 08/19/2019
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 8b22f3aaf706fa096f6c25ab8e9fdab6dc512cd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208800"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Převod projektů ze smíšeného režimu do čistého IL (Intermediate Language)

Všechny projekty C++ Visual CLR standardně odkazují na knihovny run-time jazyka C. V důsledku toho jsou tyto projekty klasifikovány jako aplikace v kombinovaném režimu, protože kombinují nativní kód s kódem, který je cílen na společný jazykový modul runtime (spravovaný kód). Při kompilaci jsou kompilovány do jazyka IL (Intermediate Language), označované také jako jazyk MSIL (Microsoft Intermediate Language).

> [!IMPORTANT]
> Visual Studio 2015 zastaralá a Visual Studio 2017 už nepodporují vytváření typů **/clr: Pure** nebo **/clr: Safe** pro aplikace CLR. Pokud požadujete čistá nebo bezpečná sestavení, doporučujeme, abyste aplikaci přeložili C#na.

Pokud používáte starší verzi sady nástrojů Microsoft C++ Compiler, která podporuje/CLR: **Pure** nebo **/clr: Safe**, můžete použít tento postup k převedení kódu na čistě MSIL:

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Převod aplikace ve smíšeném režimu do čistého mezilehlého jazyka

1. Odeberte odkazy na [knihovny run-time jazyka C](../c-runtime-library/crt-library-features.md) (CRT):

   1. V souboru. cpp definujícím vstupní bod aplikace změňte vstupní bod na `Main()`. Použití `Main()` označuje, že projekt neodkazuje na CRT.

   2. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a v místní nabídce vyberte **vlastnosti** , čímž otevřete stránky vlastností aplikace.

   3. Na stránce **Upřesnit** vlastnost projektu pro **linker**vyberte **vstupní bod** a potom do tohoto pole zadejte **Main (hlavní** ).

   4. Pro konzolové aplikace na stránce vlastností projekt **systému** pro **linker**vyberte pole **subsystému** a změňte to na **Console (/SUBSYSTEM: Console)** .

      > [!NOTE]
      > Tuto vlastnost nemusíte nastavovat pro aplikace model Windows Forms, protože pole **subsystému** je ve výchozím nastavení nastavené na **Windows (/SUBSYSTEM: Windows)** .

   5. V souboru *stdafx. h*Odkomentujte všechny příkazy `#include`. Například v konzolových aplikacích:

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       -nebo-

       Například v model Windows Formsch aplikacích:

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. V případě aplikací model Windows Forms v poli Form1. cpp přidejte komentář k příkazu `#include`, který odkazuje na Windows. h. Příklad:

      ```cpp
      // #include <windows.h>
      ```

2. Do souboru *stdafx. h*přidejte následující kód:

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Odebrat všechny nespravované typy:

   Všude, kde je to vhodné, nahraďte nespravované typy odkazy na struktury z oboru názvů [System](/dotnet/api/system) . Společné spravované typy jsou uvedeny v následující tabulce:

   |Struktura|Popis|
   |---------------|-----------------|
   |[Datového](/dotnet/api/system.boolean)|Představuje logickou hodnotu.|
   |[Bytové](/dotnet/api/system.byte)|Představuje 8 bitů unsigned integer.|
   |[Char](/dotnet/api/system.char)|Představuje znak Unicode.|
   |[Hodnotu](/dotnet/api/system.datetime)|Představuje okamžitý čas, obvykle vyjádřený jako datum a denní dobu.|
   |[Notaci](/dotnet/api/system.decimal)|Představuje desetinné číslo.|
   |[Klepat](/dotnet/api/system.double)|Představuje číslo s plovoucí desetinnou čárkou a dvojitou přesností.|
   |[Hlavních](/dotnet/api/system.guid)|Představuje globálně jedinečný identifikátor (GUID).|
   |[Int16](/dotnet/api/system.int16)|Představuje 16bitové celé číslo se znaménkem.|
   |[Uvedena](/dotnet/api/system.int32)|Představuje 32 celé číslo se znaménkem.|
   |[Int64](/dotnet/api/system.int64)|Představuje 64 celé číslo se znaménkem.|
   |[IntPtr](/dotnet/api/system.intptr)|Typ specifický pro platformu, který se používá k reprezentaci ukazatele nebo popisovače.|
   |[SByte](/dotnet/api/system.byte)|Představuje 8bitové celé číslo se znaménkem.|
   |[Konkrétní](/dotnet/api/system.single)|Představuje číslo s plovoucí desetinnou čárkou s jednoduchou přesností.|
   |[TimeSpan](/dotnet/api/system.timespan)|Představuje časový interval.|
   |[UInt16](/dotnet/api/system.uint16)|Představuje 16 bitů unsigned integer.|
   |[UInt32](/dotnet/api/system.uint32)|Představuje 32-bit unsigned integer.|
   |[UInt64](/dotnet/api/system.uint64)|Představuje 64-bit unsigned integer.|
   |[UIntPtr](/dotnet/api/system.uintptr)|Typ specifický pro platformu, který se používá k reprezentaci ukazatele nebo popisovače.|
   |[Šekem](/dotnet/api/system.void)|Označuje metodu, která nevrací hodnotu. To znamená, že metoda má návratový typ void.|
