---
title: 'Postupy: přímé vytváření instancí komponent knihovny WRL přímo | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 133f0f4ee4efed71c530c7e9e8c367c7d2031433
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013272"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Postupy: Přímé vytváření instancí komponent knihovny WRL
Další informace o použití Windows Runtime C++ šablony knihovny (WRL)[Microsoft::WRL:: Make](../windows/make-function.md) a [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) pro vytvoření instance komponenty z modulu, který ji definuje.  
  
 Pokud není zapotřebí používat továrny tříd nebo jiné mechanismy, je možné přímým vytvořením instance komponenty snížit režii. Můžete vytvořit instanci komponenty přímo v obou aplikací pro univerzální platformu Windows a v aplikacích klasické pracovní plochy.  
  
Další informace o použití knihovny šablon jazyka C++ Windows Runtime k vytvoření klasické komponenty COM a vytvoření instance z externí aplikace pracovní plochy, najdete v článku [postupy: vytvoření klasické komponenty COM](../windows/how-to-create-a-classic-com-component-using-wrl.md).  
  
 Tento dokument popisuje dva příklady. První příklad používá pro vytvoření instance komponenty funkci `Make`. V druhém příkladu se pro vytvoření instance komponenty, která může v průběhu vytváření selhat, používá funkce `MakeAndInitialize`. (Protože komponenta COM obvykle používá hodnoty HRESULT, místo výjimek, k označení chyby, typu modelu COM nevyvolá ze svého konstruktoru. `MakeAndInitialize` povoluje komponentě ověření argumentů při vytváření skrze metodu `RuntimeClassInitialize`.) Oba příklady definují rozhraní pro základní nástroj pro protokolování a implementují rozhraní definicí třídy, které zapisuje zprávy do konzoly.  
  
> [!IMPORTANT]
>  Nelze použít **nové** operátor přímé vytváření instancí komponent knihovny šablon jazyka C++ Windows Runtime. Proto je doporučeno pro přímé vytvoření instance komponenty vždy používat `Make` nebo `MakeAndInitialize`.  
  
### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Vytvoření instance komponenty pro základní nástroj pro protokolování  
  
1.  V sadě Visual Studio, vytvořit **Konzolová aplikace Win32** projektu. Název projektu, například *WRLLogger*.  
  
2.  Přidat **soubor Midl (.idl)** do projektu, zadejte název souboru `ILogger.idl`a následně přidejte následující kód:  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  Pomocí následujícího kódu nahraďte obsah `WRLLogger.cpp`.  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Zpracování chyby při vytváření komponenty základního nástroje pro protokolování  
  
1.  Pro nahrazení definice třídy `CConsoleWriter` použijte následující kód. Tato verze obsahuje členskou proměnnou soukromého řetězce a přepisuje metodu `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` selže, pokud selže volání `SHStrDup`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  Pro nahrazení definice `wmain` použijte následující kód. Tato verze používá `MakeAndInitialize` pro vytvoření instance `CConsoleWriter` objektu a ověří výsledek HRESULT.  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL:: Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)