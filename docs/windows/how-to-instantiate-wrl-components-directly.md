---
title: 'Postupy: vytváření instancí komponent knihovny WRL přímo | Microsoft Docs'
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
ms.openlocfilehash: 127a8430e79e7963ea94646f70179df2f30450ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Postupy: Přímé vytváření instancí komponent knihovny WRL
Další informace o použití Windows Runtime C++ šablony knihovny (WRL)[Microsoft::WRL::Make](../windows/make-function.md) a [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) funkce pro vytvoření instance součásti z modulu, Definuje ho.  
  
 Pokud není zapotřebí používat továrny tříd nebo jiné mechanismy, je možné přímým vytvořením instance komponenty snížit režii. Můžete vytvořit instanci komponentu přímo v obě aplikace pro univerzální platformu Windows a v aplikacích klasické pracovní plochy.  
  
Další informace o použití knihovna šablon C++ prostředí Windows Runtime vytvoření klasické komponenty COM a vytvoří instanci z externí aplikace plochy, najdete v tématu [postupy: vytvoření klasické komponenty COM](../windows/how-to-create-a-classic-com-component-using-wrl.md).  
  
 Tento dokument popisuje dva příklady. První příklad používá pro vytvoření instance komponenty funkci `Make`. V druhém příkladu se pro vytvoření instance komponenty, která může v průběhu vytváření selhat, používá funkce `MakeAndInitialize`. (Protože komponenta COM obvykle používá pro označení chyb hodnoty `HRESULT` místo výjimek, nevyvolá typ komponenty COM výjimku ze svého konstruktoru. `MakeAndInitialize` povoluje komponentě ověření argumentů při vytváření skrze metodu `RuntimeClassInitialize`.) Oba příklady definují rozhraní pro základní nástroj pro protokolování a implementují rozhraní definicí třídy, které zapisuje zprávy do konzoly.  
  
> [!IMPORTANT]
>  Nelze použít `new` operátor k vytváření instancí komponent knihovna šablon C++ prostředí Windows Runtime. Proto je doporučeno pro přímé vytvoření instance komponenty vždy používat `Make` nebo `MakeAndInitialize`.  
  
### <a name="to-create-and-instantiate-a-basic-logger-component"></a>Vytvoření instance komponenty pro základní nástroj pro protokolování  
  
1.  V sadě Visual Studio, vytvoření **Konzolová aplikace Win32** projektu. Název projektu, například `WRLLogger`.  
  
2.  Přidat **soubor Midl (.)** souboru do projektu, zadejte název souboru `ILogger.idl`a poté přidejte tento kód:  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  Pro nahrazení obsahu souboru WRLLogger.cpp použijte následující kód.  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>Zpracování chyby při vytváření komponenty základního nástroje pro protokolování  
  
1.  Pro nahrazení definice třídy `CConsoleWriter` použijte následující kód. Tato verze obsahuje členskou proměnnou soukromého řetězce a přepisuje metodu `RuntimeClass::RuntimeClassInitialize`. `RuntimeClassInitialize` selže, pokud selže volání `SHStrDup`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  Pro nahrazení definice `wmain` použijte následující kód. Tato verze pro vytvoření instance objektu `MakeAndInitialize` používá `CConsoleWriter` a provádí kontrolu výsledku `HRESULT`.  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)