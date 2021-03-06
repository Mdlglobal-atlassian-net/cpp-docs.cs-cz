---
title: 'Postupy: Vytvořit ověřitelný C++ projekty (C++vyhodnocovací)'
ms.date: 11/04/2016
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual Studio C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
ms.openlocfilehash: 0784e6f202750e846c75434eef62a12dab3952f1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448108"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Postupy: Vytvoření ověřitelných C++ projekty (C++vyhodnocovací)

Průvodci aplikací Visual C++ Vytvoření ověřitelných projektů.

> [!IMPORTANT]
> Zastaralé Visual Studio 2015 a Visual Studio 2017 se nepodporuje **/CLR: pure** a **/CLR: safe** Vytvoření ověřitelných projektů. Pokud budete potřebovat ověřitelný kód, doporučujeme že překlad kódu jazyka C#.

Ale pokud používáte starší verzi agenta Microsoft C++ sada nástrojů kompilátoru, který podporuje **/CLR: pure** a **/CLR: safe**, projekty lze převést na být možné ověřit. Toto téma popisuje, jak nastavit vlastnosti projektu a upravte zdrojové soubory projektu pro Visual Studio transformaci C++ projekty vytvářet ověřitelný aplikace.

## <a name="compiler-and-linker-settings"></a>Nastavení kompilátoru a linkeru

Ve výchozím nastavení projekty .NET pomocí příznaku/CLR kompilátoru a linkeru, aby cílový x86 hardwarové konfigurace. Ověřitelný kód musíte použít příznak/clr: safe. proto musí dát pokyn linkeru, aby generoval místo nativních strojové instrukce jazyka MSIL.

### <a name="to-change-the-compiler-and-linker-settings"></a>Chcete-li změnit nastavení kompilátoru a linkeru

1. Zobrazte stránku vlastností projektu. Další informace najdete v tématu [nastavení kompilátoru a vlastnosti sestavení](../build/working-with-project-properties.md).

1. Na **Obecné** stránky **vlastnosti konfigurace** sady uzlů, **Common Language Runtime Support** vlastnost **bezpečné společný jazyk MSIL Podpora modulu CLR (/ CLR: safe)**.

1. Na **Upřesnit** stránky **Linkeru** sady uzlů, **typ bitové kopie CLR** vlastnost **vynutit bezpečnou bitovou kopii IL (/ CLRIMAGETYPE: safe)**.

## <a name="removing-native-data-types"></a>Odebírání nativních datových typů

Protože nativní datové typy jsou neověřitelného, i v případě, že je ve skutečnosti nepoužili, musíte odebrat všechny soubory záhlaví obsahující nativní typy.

> [!NOTE]
> Následující postup platí pro projekty Windows Forms aplikace (.NET) a aplikace konzoly (.NET).

### <a name="to-remove-references-to-native-data-types"></a>Chcete-li odebrat odkazy na nativní datové typy

1. Všechno, co v souboru Stdafx.h komentář.

## <a name="configuring-an-entry-point"></a>Konfigurace vstupního bodu

Protože ověřitelné aplikace nemůže používat knihovny run-time C (CRT), nelze jsou závislé na CRT, které volá funkci main jako standardní vstupní bod. To znamená, že je nutné explicitně zadat název funkce, která má být volána na začátku linkeru. (V tomto případě Main() místo main() nebo _tmain() slouží k označení non-CRT vstupního bodu, ale protože vstupní bod musí být explicitně určeny, tento název je volitelný.)

> [!NOTE]
> Následující postupy platí pro projekty aplikace konzoly (.NET).

#### <a name="to-configure-an-entry-point"></a>Konfigurace vstupního bodu

1. Změňte _tmain() Main() v souboru hlavní .cpp v projektu.

1. Zobrazte stránku vlastností projektu. Další informace najdete v tématu [nastavení kompilátoru a vlastnosti sestavení](../build/working-with-project-properties.md).

1. Na **Upřesnit** stránky **Linkeru** uzlu, zadejte `Main` jako **vstupní bod** hodnotu vlastnosti.

## <a name="see-also"></a>Viz také:

- [Čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
