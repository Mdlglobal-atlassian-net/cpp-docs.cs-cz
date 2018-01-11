---
title: "Postupy: zpracování událostí s použitím knihovny WRL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3341992ce2b10897fca165a787e568b5e0bc660
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-handle-events-using-wrl"></a>Postupy: Zpracování událostí s použitím knihovny WRL
Tento dokument ukazuje, jak používat k přihlášení k odběru a zpracování událostí objektu prostředí Windows Runtime Windows Runtime C++ šablony knihovny (WRL).  
  
 Více základní příklad, který vytvoří instanci této součásti a načte hodnotu vlastnosti najdete v tématu [postupy: Aktivace a používání komponent prostředí Windows Runtime](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
## <a name="subscribing-to-and-handling-events"></a>Přihlášení k odběru a zpracování událostí  
 Následující kroky počáteční `ABI::Windows::System::Threading::IDeviceWatcher` objektu a sledovat průběh pomocí obslužných rutin událostí. `IDeviceWatcher` Rozhraní umožňuje výčet zařízení, nebo asynchronně na pozadí a přijímat oznámení, když jsou zařízení přidat, odebrat nebo změnit. [Zpětného volání](../windows/callback-function-windows-runtime-cpp-template-library.md) funkce je důležitou součástí tohoto příkladu, protože umožňuje ji k určení obslužné rutiny událostí, které zpracovávají výsledky operace na pozadí. Úplný příklad následuje.  
  
> [!WARNING]
>  I když používáte obvykle Windows knihovna šablon C++ Runtime v aplikaci pro univerzální platformu Windows, tento příklad používá konzolovou aplikaci pro obrázek. Funkce, jako `wprintf_s` nejsou k dispozici z aplikace pro univerzální platformu Windows. Další informace o typy a funkce, které můžete použít v aplikaci pro univerzální platformu Windows najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) a [aplikace Win32 a COM pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
1.  Zahrnout (`#include`) potřebné prostředí Windows Runtime, knihovna šablon C++ prostředí Windows Runtime nebo standardní knihovna C++ hlavičky.  
  
     [!code-cpp[wrl-consume-event#2](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]  
  
     Windows.Devices.Enumeration.h deklaruje typy, které jsou nutné k vytvoření výčtu zařízení.  
  
     Doporučujeme vám, že využíváte `using namespace` v soubor tak čitelnost kód direktivy.  
  
2.  Přidejte místní proměnné pro aplikaci. Tento příklad obsahuje počet počet výčtové zařízení a registrace tokenů, které umožní, aby později odhlášení odběru událostí.  
  
     [!code-cpp[wrl-consume-event#7](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]  
  
3.  Inicializujte prostředí Windows Runtime.  
  
     [!code-cpp[wrl-consume-event#3](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]  
  
4.  Vytvoření [událostí](../windows/event-class-windows-runtime-cpp-template-library.md) objekt, který se synchronizuje se na dokončení procesu výčtu k hlavní aplikaci.  
  
     [!code-cpp[wrl-consume-event#4](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Tato událost je pro demonstrační pouze jako součást konzolovou aplikaci. Tento příklad používá událost zajistit, že před ukončí aplikaci dokončení asynchronní operace. Ve většině aplikací je obvykle není počkat na dokončení asynchronních operací.  
  
5.  Vytváření aktivace pro `IDeviceWatcher` rozhraní.  
  
     [!code-cpp[wrl-consume-event#5](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]  
  
     Prostředí Windows Runtime používá k identifikaci typy plně kvalifikované názvy. `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` Parametr je řetězec, který poskytuje prostředí Windows Runtime a obsahuje název modulu runtime požadované třídy.  
  
6.  Vytvořte `IDeviceWatcher` objektu.  
  
     [!code-cpp[wrl-consume-event#6](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]  
  
7.  Použití `Callback` funkce pro přihlášení k odběru `Added`, `EnumerationCompleted`, a `Stopped` události.  
  
     [!code-cpp[wrl-consume-event#8](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]  
  
     `Added` Obslužné rutiny události zvýší počet výčtové zařízení. Když nejsou nalezeny deset zařízení zastaví proces výčtu.  
  
     `Stopped` Obslužné rutiny události odebere obslužné rutiny událostí a nastaví událost dokončení.  
  
     `EnumerationCompleted` Obslužné rutiny události zastaví proces výčtu. Jsme zpracování této události v případě, že méně než deset zařízení.  
  
    > [!TIP]
    >  Tento příklad používá k definování zpětná volání výrazu lambda. Můžete použít také funkci objekty (functors), ukazatelů na funkce, nebo [std::function](../standard-library/function-class.md) objekty. Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
8.  Spusťte proces výčtu.  
  
     [!code-cpp[wrl-consume-event#9](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]  
  
9. Počkejte na dokončení a poté vytiskněte zprávu procesu výčtu. Všechny `ComPtr` a RAII objekty nechte oboru a vydávají automaticky.  
  
     [!code-cpp[wrl-consume-event#10](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]  
  
 Tady je kompletní příklad:  
  
 [!code-cpp[wrl-consume-event#1](../windows/codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kompilace kódu, zkopírujte jej a vložte ji do projektu sady Visual Studio nebo ho vložte do souboru, který je pojmenován `wrl-consume-events.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe knihovny wrl využívat events.cpp runtimeobject.lib**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)