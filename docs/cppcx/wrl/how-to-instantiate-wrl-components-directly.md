---
title: 'Postupy: Přímé vytváření instancí komponent knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: f291e982d7f77c63821e5943a5867662ccd1b4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213899"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Postupy: Přímé vytváření instancí komponent knihovny WRL

Naučte se používat knihovnu šablon C++ prostředí Windows Runtime (WRL)[Microsoft:: WRL:: Make](make-function.md) a [Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md) pro vytvoření instance komponenty z modulu, který ji definuje.

Pokud není zapotřebí používat továrny tříd nebo jiné mechanismy, je možné přímým vytvořením instance komponenty snížit režii. Komponentu lze vytvořit přímo v aplikacích Univerzální platforma Windows i v aplikacích klasické pracovní plochy.

Další informace o tom, jak C++ pomocí knihovny šablon prostředí Windows Runtime vytvořit klasickou komponentu modelu COM a vytvořit její instanci z externí desktopové aplikace, najdete v tématu [How to: Create a Classic komponent modelu COM](how-to-create-a-classic-com-component-using-wrl.md).

Tento dokument popisuje dva příklady. První příklad používá pro vytvoření instance komponenty funkci `Make`. V druhém příkladu se pro vytvoření instance komponenty, která může v průběhu vytváření selhat, používá funkce `MakeAndInitialize`. (Vzhledem k tomu, že model COM obvykle používá hodnoty HRESULT namísto výjimek, k indikaci chyb, typ modelu COM obvykle nevyvolává z jeho konstruktoru. `MakeAndInitialize` umožňuje komponentě ověřit argumenty konstrukce pomocí metody `RuntimeClassInitialize`.) Oba příklady definují základní rozhraní pro protokolovací nástroj a implementují toto rozhraní definováním třídy, která zapisuje zprávy do konzoly.

> [!IMPORTANT]
> Operátor `new` nelze použít k vytvoření instance prostředí Windows Runtime C++ součástí knihovny šablon. Proto je doporučeno pro přímé vytvoření instance komponenty vždy používat `Make` nebo `MakeAndInitialize`.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Vytvoření instance komponenty pro základní nástroj pro protokolování

1. V aplikaci Visual Studio vytvořte projekt **konzolové aplikace Win32** . Pojmenujte projekt, například *WRLLogger*.

2. Do projektu přidejte soubor **MIDL (. idl)** , pojmenujte soubor `ILogger.idl`a pak přidejte tento kód:

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. K nahrazení obsahu `WRLLogger.cpp`použijte následující kód.

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Zpracování chyby při vytváření komponenty základního nástroje pro protokolování

1. Pro nahrazení definice třídy `CConsoleWriter` použijte následující kód. Tato verze obsahuje členskou proměnnou soukromého řetězce a přepisuje metodu `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` dojde k chybě, pokud volání `SHStrDup` neproběhne úspěšně.

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Pro nahrazení definice `wmain` použijte následující kód. Tato verze používá `MakeAndInitialize` k vytvoření instance `CConsoleWriter` objektu a kontroluje výsledek HRESULT.

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft:: WRL:: make](make-function.md)<br/>
[Microsoft:: WRL::D etails:: MakeAndInitialize](makeandinitialize-function.md)
