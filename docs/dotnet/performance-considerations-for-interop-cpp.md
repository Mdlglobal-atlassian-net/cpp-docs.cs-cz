---
title: Faktory ovlivňující výkon u zprostředkovatelů komunikace (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: addf3fbc5f6261800ceebf6e8bb1abe1a64f245e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478205"
---
# <a name="performance-considerations-for-interop-c"></a>Faktory ovlivňující výkon u zprostředkovatelů komunikace (C++)

Toto téma obsahuje pokyny pro snižuje vliv na výkon za běhu spravovaného a nespravovaného spolupráce přechody.

Jazyk Visual C++ podporuje stejné mechanismy spolupráce jako dalších jazycích .NET, například Visual Basic a C# (nespravovaného), ale přináší také spolupráce podpory, které jsou specifické pro Visual C++ (zprostředkovatele komunikace C++). Pro kritickém pro výkon aplikace je důležité si uvědomit důsledky výkon jednotlivých spolupráce techniky.

Bez ohledu na to spolupráce techniku použít sekvence speciální přechodu, nazvané převody, jsou požadovány pokaždé, když spravované funkce volá nespravovaný versa funkce a naopak. Tyto převody jsou automaticky vložen kompilátorem jazyka Visual C++, ale je důležité si pamatovat, že kumulativně, můžou být tyto přechody náročné z hlediska výkonu.

## <a name="reducing-transitions"></a>Omezení přechodů

Jedním ze způsobů k zamezení nebo snížit náklady na vzájemné spolupráce převodní rutiny je refaktorovat používané, chcete-li minimalizovat spravovaného a nespravovaného přechody rozhraní. Výraznému zlepšení výkonu je možné provádět pomocí cílení chatty rozhraní, které jsou ty, které se podílejí častých volání přes hranice spravovaného a nespravovaného. Spravované funkce, která volá nespravovanou funkci v těsné smyčce, například je vhodným kandidátem pro refaktoring. Pokud je smyčka samotná se přesune do nespravované oblasti nebo pokud spravované alternativy k nespravovaného volání je vytvořen (možná fronta dat na straně spravované a jejich zařazování do nespravované rozhraní API najednou po smyčce), může být počet přechodů snižuje přihlašování ificantly.

## <a name="pinvoke-vs-c-interop"></a>P/Invoke vs. interoperabilita C++

Pro jazyky .NET, jako je například Visual Basic a C# je předepsané způsob spolupráce s nativními komponentami P/Invoke. Protože P/Invoke je podporovaný rozhraním .NET Framework, Visual C++ podporuje také, ale vlastní podporu interoperabilitu, která se označuje jako zprostředkovatele komunikace C++ poskytuje jazyk Visual C++. Zprostředkovatele komunikace C++ je upřednostňována před P/Invoke, protože deklarace P/Invoke není typově bezpečný. V důsledku toho jsou primárně hlášeny chyby za běhu, ale zprostředkovatele komunikace C++ má také výhody výkonu prostřednictvím P/Invoke.

Obě tyto metody vyžadují několik věcí, která se provede při každém spravované funkce bude volat nespravovanou funkci:

- Argumenty volání funkce jsou zařazeny z modulu CLR do nativních typů.

- Spravované na nespravované převodní rutina se spustí.

- Nespravovaná funkce je volána (pomocí nativní verze argumenty).

- Je provedena převodu nespravovaného do spravovaného.

- Návratový typ a jakékoli "out" nebo "v, out" argumenty jsou zařazovat z nativního pro typy CLR.

Spravovaného a nespravovaného převody jsou nezbytné pro spolupráci s k práci, ale data zařazování, který je požadován závisí na datové typy, které jsou zapojené, podpis funkce a použití dat.

Zařazování dat, které se provádí pomocí zprostředkovatele komunikace C++ je možné nejjednodušším: parametry jsou jednoduše zkopírovat přes hranice spravovaného a nespravovaného bitový způsobem; není provedena žádná transformace. Pro deklarace P/Invoke, toto je pouze hodnotu true, pokud všechny parametry jsou jednoduché, přenositelné typy. V opačném případě P/Invoke provádí nepříliš robustní kroky pro každý spravovaný parametr převést na odpovídající nativní typ, a naopak v případě, že argumenty jsou označeny jako "out" nebo "v, out".

Jinými slovy zprostředkovatele komunikace C++ používá nejrychlejší možné metodu zařazování dat, zatímco používá nejrobustnější metoda P/Invoke. To znamená, že ve výchozím nastavení zprostředkovatele komunikace C++ (v podobě typické pro jazyk C++) poskytuje optimální výkon a adresování případy, ve kterém toto chování není bezpečné nebo vhodné zodpovídá programátor.

Zprostředkovatele komunikace C++ proto vyžaduje, aby zařazování dat musí být zadaná explicitně, ale výhodou je, že je programátorovi mohou rozhodnout, co je vhodné, vzhledem k povaze dat a jak se má použít. Kromě toho Ačkoli chování zařazování dat P/Invoke lze upravovat při přizpůsobit tak, aby takovou úroveň důvěryhodnosti, zprostředkovatele komunikace C++ umožňuje přizpůsobit na základě volání za voláním zařazování dat. To není možné s P/Invoke.

Další informace o zprostředkovatele komunikace C++, naleznete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="see-also"></a>Viz také

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)