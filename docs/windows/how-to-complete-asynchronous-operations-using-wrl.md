---
title: "Postupy: dokončení asynchronních operací s použitím knihovny WRL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c505c44fe18f75eeb64c6b31ca222405f570761
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Postupy: Dokončení asynchronních operací s použitím knihovny WRL
Tento dokument ukazuje, jak použít Windows Runtime C++ šablony knihovny (WRL) ke spuštění asynchronní operace a práci při dokončení operace.  
  
 Tento dokument popisuje dva příklady. V prvním příkladu spouští asynchronní časovače a čeká časovač vyprší. V tomto příkladu zadejte asynchronní akce při vytváření objektu časovače. V druhém příkladu spustí pracovní vlákna na pozadí. Tento příklad ukazuje, jak pracovat s prostředí Windows Runtime metodu, která vrátí `IAsyncInfo` rozhraní. [Zpětného volání](../windows/callback-function-windows-runtime-cpp-template-library.md) funkce je důležitou součástí oba příklady, protože umožňuje, aby zadejte obslužné rutiny události ke zpracování výsledků asynchronních operací.  
  
 Více základní příklad, který vytvoří instanci komponenty a načte hodnotu vlastnosti najdete v tématu [postupy: Aktivace a používání komponent prostředí Windows Runtime](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
> [!TIP]
>  Tyto příklady použití výrazů lambda můžete definovat zpětných volání. Můžete použít také funkci objekty (functors), ukazatelů na funkce, nebo [std::function](../standard-library/function-class.md) objekty. Další informace o výrazy lambda C++ najdete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="example-working-with-a-timer"></a>Příklad: Práce s časovačem  
 Následující postup spuštění asynchronní časovače a čekání na časovač vyprší. Úplný příklad následuje.  
  
> [!WARNING]
>  I když používáte obvykle Windows knihovna šablon C++ Runtime v aplikaci pro univerzální platformu Windows, tento příklad používá konzolovou aplikaci pro obrázek. Funkce, jako `wprintf_s` nejsou k dispozici z aplikace pro univerzální platformu Windows. Další informace o typy a funkce, které můžete použít v aplikaci pro univerzální platformu Windows najdete v tématu [funkcí CRT nepodporuje /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) a [aplikace Win32 a COM pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
1.  Zahrnout (`#include`) potřebné prostředí Windows Runtime, knihovna šablon C++ prostředí Windows Runtime nebo standardní knihovna C++ hlavičky.  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     Windows.System.Threading.h deklaruje typy, které jsou nutné k použití asynchronní časovače.  
  
     Doporučujeme vám, že využíváte `using namespace` v soubor tak čitelnost kód direktivy.  
  
2.  Inicializujte prostředí Windows Runtime.  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  Vytváření aktivace pro `ABI::Windows::System::Threading::IThreadPoolTimer` rozhraní.  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     Prostředí Windows Runtime používá k identifikaci typy plně kvalifikované názvy. `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` Parametr je řetězec, který poskytuje prostředí Windows Runtime a obsahuje název modulu runtime požadované třídy.  
  
4.  Vytvoření [událostí](../windows/event-class-windows-runtime-cpp-template-library.md) objekt, který synchronizuje zpětné volání časovače k hlavní aplikaci.  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Tato událost je pro demonstrační pouze jako součást konzolovou aplikaci. Tento příklad používá událost zajistit, že před ukončí aplikaci dokončení asynchronní operace. Ve většině aplikací je obvykle není počkat na dokončení asynchronních operací.  
  
5.  Vytvoření `IThreadPoolTimer` objekt, který vyprší po dvou sekund. Použití `Callback` funkce pro vytvoření obslužné rutiny události ( `ABI::Windows::System::Threading::ITimerElapsedHandler` objekt).  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  Tisk zpráv do konzoly a počkejte zpětné volání časovače pro dokončení. Všechny `ComPtr` a RAII objekty nechte oboru a vydávají automaticky.  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 Tady je kompletní příklad:  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `wrl-consume-async.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe knihovny wrl využívat async.cpp runtimeobject.lib**  
  
## <a name="example-working-with-a-background-thread"></a>Příklad: Práce s vlákna na pozadí  
 Následující kroky spustit pracovní vlákno a definovat akci, kterou provádí tento přístup z více vláken. Úplný příklad následuje.  
  
> [!TIP]
>  Tento příklad ukazuje, jak pracovat s `ABI::Windows::Foundation::IAsyncAction` rozhraní. Tento vzor můžete použít pro všechny rozhraní, které implementuje `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, a `IAsyncOperationWithProgress`.  
  
1.  Zahrnout (`#include`) potřebné prostředí Windows Runtime, knihovna šablon C++ prostředí Windows Runtime nebo standardní knihovna C++ hlavičky.  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h deklaruje typy, které jsou nutné k použití pracovní vlákno.  
  
     Doporučujeme vám, že používáte `using namespace` v soubor tak čitelnost kód direktivy.  
  
2.  Inicializujte prostředí Windows Runtime.  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  Vytváření aktivace pro `ABI::Windows::System::Threading::IThreadPoolStatics` rozhraní.  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  Vytvoření [událostí](../windows/event-class-windows-runtime-cpp-template-library.md) objekt, který synchronizuje dokončení pracovní vlákno k hlavní aplikaci.  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  Tato událost je pro demonstrační pouze jako součást konzolovou aplikaci. Tento příklad používá událost zajistit, že před ukončí aplikaci dokončení asynchronní operace. Ve většině aplikací je obvykle není počkat na dokončení asynchronních operací.  
  
5.  Volání `IThreadPoolStatics::RunAsync` metodu pro vytvoření pracovní vlákno. Použití `Callback` funkce můžete definovat akce.  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     `IsPrime` Funkce je definována v kompletní příklad, který následuje dále.  
  
6.  Tisk zpráv do konzoly a počkat na vlákno k dokončení. Všechny `ComPtr` a RAII objekty nechte oboru a vydávají automaticky.  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 Tady je kompletní příklad:  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `wrl-consume-asyncOp.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe knihovny wrl využívat asyncOp.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)
