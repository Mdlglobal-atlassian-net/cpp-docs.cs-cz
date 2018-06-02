---
title: 'Postupy: Vytvoření ověřitelných projektů jazyka C++ (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 36e7ee85d97639df6298a346ae83bb090e81bf87
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704760"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Postupy: Vytvoření ověřitelných projektů C++ (C + +/ CLI)

Průvodci aplikací Visual C++ nevytvářejte ověřitelných projektů.

> [!IMPORTANT]
> Visual Studio 2015 nepoužívá a Visual Studio 2017 nepodporuje **/CLR: pure** a **/CLR: safe** Vytvoření ověřitelných projektů. Pokud budete potřebovat ověřitelný kód, doporučujeme, abyste že převede kódu jazyka C#.

Ale pokud používáte starší verzi sady nástrojů kompilátoru Visual C++, který podporuje **/CLR: pure** a **/CLR: safe**, projekty mohou být převedeny na ověřitelné. Toto téma popisuje, jak nastavit vlastnosti projektu a upravit projektu zdrojové soubory k transformaci projekty Visual C++ vytvářely ověřitelné aplikace.

## <a name="compiler-and-linker-settings"></a>Nastavení kompilátoru a linkeru

 Ve výchozím nastavení projekty .NET použijte příznak kompilátoru/CLR a nakonfigurujte linkeru cíl x86 hardware. Ověřitelný kód je nutné použít příznak/clr: safe a musí vyzvat linkeru pro generování MSIL místo pokynů nativní počítače.

### <a name="to-change-the-compiler-and-linker-settings"></a>Chcete-li změnit nastavení kompilátoru a linkeru

1. Zobrazí stránku vlastností projektu. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

1. Na **Obecné** v části **vlastnosti konfigurace** sada uzlů, **Common Language Runtime Support** vlastnost **bezpečné společný jazyk MSIL Podpora modulu runtime (/ CLR: safe)**.

1. Na **Upřesnit** v části **Linkeru** sada uzlů, **typ obrázku CLR** vlastnost **Force bezpečné IL image (/ CLRIMAGETYPE: safe)**.

## <a name="removing-native-data-types"></a>Odebrání nativní datové typy

Protože nativní datové typy nejsou ověřitelné, i když nejsou použity ve skutečnosti, musíte odebrat všechny soubory záhlaví obsahující nativní typy.

> [!NOTE]
> Následující postup platí pro projekty Windows Forms aplikace (.NET) a konzole aplikace (.NET).

### <a name="to-remove-references-to-native-data-types"></a>Chcete-li odebrat odkazy na nativní datové typy

1. Poznámky, které se nacházejí v souboru Stdafx.h.

## <a name="configuring-an-entry-point"></a>Konfigurace vstupního bodu

Protože ověřitelné aplikace nemůžou používat běhové knihovny jazyka C (CRT), nemůžou záviset na CRT volat funkci main jako standardní vstupní bod. To znamená, že je nutné explicitně zadat název funkce k volání původně linkeru. (V tomto případě Main() místo main() nebo _tmain() slouží k označení bez CRT vstupní bod, ale protože vstupní bod musí být explicitně určen, tento název je volitelný.)

> [!NOTE]
> Následující postupy platí pro projekty konzoly aplikace (.NET).

#### <a name="to-configure-an-entry-point"></a>Ke konfiguraci vstupního bodu

1. Změňte _tmain() na Main() v hlavní souboru projektu.

1. Zobrazí stránku vlastností projektu. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

1. Na **Upřesnit** v části **Linkeru** uzlu, zadejte `Main` jako **vstupní bod** hodnotu vlastnosti.

## <a name="see-also"></a>Viz také:

- [Čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
