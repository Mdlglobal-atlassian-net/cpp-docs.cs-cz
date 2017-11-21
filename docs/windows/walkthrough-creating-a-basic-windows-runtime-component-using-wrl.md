---
title: "Návod: Vytvoření základní komponenty prostředí Windows Runtime použitím knihovny WRL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 6e3f0986-7905-4f94-90e5-22c2ebfc8cd0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0c57e6b8ffb501ea4c6b75429bab88bbe5dc93eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-creating-a-basic-windows-runtime-component-using-wrl"></a>Postup: Vytvoření základní komponenty prostředí Windows Runtime s použitím knihovny WRL
Tento dokument ukazuje, jak používat Windows Runtime C++ šablony knihovny (WRL) k vytvoření základní komponenty prostředí Windows Runtime. Součást sečte dvě čísla a vyvolá událost, pokud je výsledek prime. Tento dokument také ukazuje, jak používat komponentu z aplikace univerzální platformu Windows, která používá jazyk JavaScript.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Prostředí s [prostředí Windows Runtime](http://msdn.microsoft.com/library/windows/apps/br211377.aspx).  
  
-   Zkušenosti s COM.  
  
### <a name="to-create-a-basic-windows-runtime-component-that-adds-two-numbers"></a>Pro vytvoření základní komponenty prostředí Windows Runtime, která sečte dvě čísla  
  
1.  V sadě Visual Studio vytvořit Visual C++ `WRLClassLibrary` projektu. Dokument [šablona projektu knihovny tříd](../windows/wrl-class-library-project-template.md) popisuje, jak stáhnout tuto šablonu. Název projektu `Contoso`.  
  
2.  V Contoso.cpp a Contoso.idl nahraďte všechny výskyty "WinRTClass" s "Kalkulačky".  
  
3.  V Contoso.idl, přidejte `Add` metodu `ICalculator` rozhraní.  
  
     [!code-cpp[wrl-basic-component#1](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_1.idl)]  
  
4.  V Contoso.cpp, přidejte `Add` metodu `public` části `Calculator` – třída.  
  
     [!code-cpp[wrl-basic-component#2](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_2.cpp)]  
  
    > [!IMPORTANT]
    >  Vzhledem k tomu, že vytváříte komponenty modelu COM, nezapomeňte použít `__stdcall` konvence volání.  
  
     Doporučujeme vám, že používáte `_Out_` a další zdroje poznámky jazyk (SAL) poznámky k popisu, jak funkce používá jeho parametry. SAL – poznámky také popisují návratové hodnoty. SAL – poznámky pracovat [nástroje Analýza kódu C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) ke zjištění možných vady C a C++ zdrojový kód. Běžné chyby kódování, které jsou hlášeny nástrojem pro zahrnout přetečení vyrovnávací paměti, neinicializovaného paměti, dereferences ukazatele null a nevracení paměti a prostředků.  
  
### <a name="to-use-the-component-from-a-universal-windows-platform-app-that-uses-javascript"></a>Používání komponent z aplikace pro univerzální platformu Windows, která využívá JavaScript  
  
1.  V sadě Visual Studio, přidejte nový JavaScript `Blank App` projektu do `Contoso` řešení. Název projektu `CalculatorJS`.  
  
2.  V `CalculatorJS` projekt, přidejte odkaz na `Contoso` projektu.  
  
3.  V default.html, nahraďte `body` část s těmito prvky uživatelského rozhraní:  
  
     [!code-html[wrl-basic-component#3](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_3.html)]  
  
4.  V souboru default.js, implementovat `OnClick` funkce.  
  
     [!code-javascript[wrl-basic-component#4](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_4.js)]  
  
    > [!NOTE]
    >  V jazyce JavaScript se změní první písmeno názvu metoda tak, aby odpovídaly standardní zásady vytváření názvů na malá písmena.  
  
### <a name="to-add-an-event-that-fires-when-a-prime-number-is-calculated"></a>Chcete-li přidat událost, která aktivuje se v případě, že se počítá prime číslo  
  
1.  V Contoso.idl před deklaraci `ICalculator`, definování typu delegáta `PrimeNumberEvent`, který poskytuje `int` argument.  
  
     [!code-cpp[wrl-basic-component#5](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_5.idl)]  
  
     Při použití `delegate` – klíčové slovo, MIDL kompilátoru vytvoří rozhraní, které obsahuje `Invoke` metodu, která odpovídá podpis tohoto delegáta. V tomto příkladu vygenerovaný soubor Contoso_h.h definuje `IPrimeNumberEvent` rozhraní, které se používá později v tomto postupu.  
  
     [!code-cpp[wrl-basic-component#13](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_6.cpp)]  
  
2.  V `ICalculator` rozhraní, zadejte `PrimeNumberFound` událostí. `eventadd` a `eventremove` atributy určit, že příjemce `ICalculator` rozhraní můžete přihlásit k odběru i odhlásit z této události.  
  
     [!code-cpp[wrl-basic-component#6](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_7.idl)]  
  
3.  V Contoso.cpp, přidejte `private` [Microsoft::WRL::EventSource](../windows/eventsource-class.md) členské proměnné ke správě události odběratele a vyvolat obslužnou rutinu události.  
  
     [!code-cpp[wrl-basic-component#7](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_8.cpp)]  
  
4.  V Contoso.cpp, implementovat `add_PrimeNumberFound` a `remove_PrimeNumberFound` metody.  
  
     [!code-cpp[wrl-basic-component#8](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_9.cpp)]  
  
### <a name="to-raise-the-event-when-a-prime-number-is-calculated"></a>Pro vyvolání události při výpočtu prime číslo  
  
1.  V Contoso.cpp, přidejte `IsPrime` metodu `private` části `Calculator` – třída.  
  
     [!code-cpp[wrl-basic-component#12](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_10.cpp)]  
  
2.  Změnit `Calculator`na `Add` metoda k volání [Microsoft::WRL::EventSource::InvokeAll](../windows/eventsource-invokeall-method.md) metoda při výpočtu prime číslo.  
  
     [!code-cpp[wrl-basic-component#11](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_11.cpp)]  
  
### <a name="to-handle-the-event-from-javascript"></a>Zpracování události z jazyka JavaScript  
  
1.  V default.html, upravte `body` přidány textová oblast, která obsahuje prvočísel.  
  
     [!code-html[wrl-basic-component#9](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_12.html)]  
  
2.  V souboru default.js, změnit `Add` funkce pro zpracování `PrimeNumberFound` událostí. Obslužné rutiny události připojí číslo prime textová oblast, která byla definována v předchozím kroku.  
  
     [!code-javascript[wrl-basic-component#10](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_13.js)]  
  
    > [!NOTE]
    >  V jazyce JavaScript názvy událostí se změnil na malá a se přidá jako předpona s "na" tak, aby odpovídaly standardní zásady vytváření názvů.  
  
 Následující obrázek znázorňuje základní kalkulačky aplikaci.  
  
 ![Základní kalkulačky aplikací pomocí jazyka JavaScript](../windows/media/wrl_basic_component.png "WRL_Basic_Component")  
  
## <a name="next-steps"></a>Další kroky  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Šablona projektu knihovny tříd](../windows/wrl-class-library-project-template.md)   
 [Nástroj pro analýzu kódu C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)