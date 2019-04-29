---
title: 'Postupy: Přímo přímé vytváření instancí komponent knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: 3f622a79aed6a1e42feccb92e1a01b3bc1277151
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398300"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Postupy: Přímo přímé vytváření instancí komponent knihovny WRL

Další informace o použití Windows Runtime C++ šablony knihovny (WRL)[Microsoft::WRL:: Make](make-function.md) a [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) pro vytvoření instance komponenty z modulu, který ji definuje.

Pokud není zapotřebí používat továrny tříd nebo jiné mechanismy, je možné přímým vytvořením instance komponenty snížit režii. Můžete vytvořit instanci komponenty přímo v obou aplikací pro univerzální platformu Windows a v aplikacích klasické pracovní plochy.

Další informace o použití knihovny šablon jazyka C++ Windows Runtime k vytvoření klasické komponenty COM a vytvoření instance z externí aplikace pracovní plochy, najdete v článku [jak: Vytvoření klasické komponenty COM](how-to-create-a-classic-com-component-using-wrl.md).

Tento dokument popisuje dva příklady. První příklad používá pro vytvoření instance komponenty funkci `Make`. V druhém příkladu se pro vytvoření instance komponenty, která může v průběhu vytváření selhat, používá funkce `MakeAndInitialize`. (Protože komponenta COM obvykle používá hodnoty HRESULT, místo výjimek, k označení chyby, typu modelu COM nevyvolá ze svého konstruktoru. `MakeAndInitialize` povoluje komponentě ověření argumentů při vytváření skrze `RuntimeClassInitialize` metoda.) Oba příklady definují rozhraní pro základní nástroj pro protokolování a implementují rozhraní definicí třídy, které zapisuje zprávy do konzoly.

> [!IMPORTANT]
> Nelze použít `new` operátor přímé vytváření instancí komponent knihovny šablon jazyka C++ Windows Runtime. Proto je doporučeno pro přímé vytvoření instance komponenty vždy používat `Make` nebo `MakeAndInitialize`.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Vytvoření instance komponenty pro základní nástroj pro protokolování

1. V sadě Visual Studio, vytvořit **Konzolová aplikace Win32** projektu. Název projektu, například *WRLLogger*.

2. Přidat **soubor Midl (.idl)** do projektu, zadejte název souboru `ILogger.idl`a následně přidejte následující kód:

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. Pomocí následujícího kódu nahraďte obsah `WRLLogger.cpp`.

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Zpracování chyby při vytváření komponenty základního nástroje pro protokolování

1. Pro nahrazení definice třídy `CConsoleWriter` použijte následující kód. Tato verze obsahuje členskou proměnnou soukromého řetězce a přepisuje metodu `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` Pokud selže volání `SHStrDup` selže.

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Pro nahrazení definice `wmain` použijte následující kód. Tato verze používá `MakeAndInitialize` pro vytvoření instance `CConsoleWriter` objektu a ověří výsledek HRESULT.

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Viz také:

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft::WRL::Make](make-function.md)<br/>
[Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)