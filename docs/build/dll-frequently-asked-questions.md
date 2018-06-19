---
title: MFC DLL – nejčastější dotazy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f5740989562aea799f3a49adfa464e2c460acb3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372507"
---
# <a name="dll-frequently-asked-questions"></a>DLL – nejčastější dotazy  
  
Následující jsou uvedeny některé časté otázky (FAQ) o knihovny DLL.  
    
-   [Může knihovna MFC DLL vytvořit více vláken?](#mfc_multithreaded_1)  

-   [Může Vícevláknová aplikace přistupovat ke knihovně MFC DLL v různých vláknech?](#mfc_multithreaded_2)  
  
-   [Máte nějaká MFC – třídy nebo funkce, které nelze použít v knihovně MFC DLL?](#mfc_prohibited_classes)  
  
-   [Jaké optimalizační techniky mám použít ke zlepšení výkonu klientské aplikace při načítání?](#mfc_optimization)  
  
-   [Nevracení paměti je v mé běžné knihovny MFC DLL, ale vlastního kódu vypadá dobře. Jak můžete najít nevrácená paměť systému?](#memory_leak)  

## <a name="mfc_multithreaded_1"></a> Může knihovna MFC DLL vytvořit více vláken?  
  
S výjimkou při inicializaci knihovny MFC DLL bezpečně vytvořit více vláken také používá místní úložiště (TLS) funguje jako Win32 vlákno **TlsAlloc** přidělit úložiště thread local. Ale pokud knihovně MFC DLL používá **__declspec(thread)** přidělit úložiště thread local, musí být implicitně propojena klientská aplikace na knihovnu DLL. Pokud klientská aplikace explicitně odkazuje na knihovnu DLL, volání **LoadLibrary** nebude úspěšně načíst knihovnu DLL. Další informace o vytváření více vláken uvnitř MFC – knihovny DLL najdete v článku znalostní báze Knowledge Base, "PRB: Volání LoadLibrary() na zatížení knihovnu DLL, má statické protokol TLS, (Q118816). Další informace o lokální proměnné vláken v knihovnách DLL najdete v tématu [vlákno](../cpp/thread.md).
  
 MFC DLL, která vytvoří nové vlákno MFC během spouštění se zastaví odezvu, když je načten jiná aplikace. To zahrnuje při každém vlákno voláním `AfxBeginThread` nebo `CWinThread::CreateThread` uvnitř:  
  
-   `InitInstance` z `CWinApp`-odvozené objekt v běžné knihovny MFC DLL.  
  
-   Zadaný `DllMain` nebo **RawDllMain** funkce v běžné knihovny MFC DLL.  
  
-   Zadaný `DllMain` nebo **RawDllMain** funkce v knihovnu DLL.  
  
 Další informace o vytváření vláken během inicializace najdete v článku znalostní báze Knowledge Base, "PRB: Nelze vytvořit MFC vláken během spouštění knihovny DLL" (Q142243).  
  
## <a name="mfc_multithreaded_2"></a> Může Vícevláknová aplikace přistupovat ke knihovně MFC DLL v různých vláknech?
Vícevláknové aplikace mají přístup k regulární knihovny MFC DLL, která dynamicky propojené s knihovnou MFC a knihovny DLL rozšíření MFC z různých vláknech. Od verze Visual C++ verze 4.2 aplikace přístup regulární knihovny MFC DLL, která staticky propojit MFC z více vláken, které jsou vytvořené v aplikaci a.  
  
 Starší než verze 4.2 pouze jedno vlákno externí připojit regulární MFC DLL, která staticky propojené do MFC. Další informace o omezení přístupu k regulární knihovny DLL MFC, který staticky propojit MFC z více vláken (před verzí Visual C++ verze 4.2), najdete v článku znalostní báze Knowledge Base "více vláken a MFC _USRDLLs" (Q122676).  
  
 Všimněte si, že pojem USRDLL se již nepoužívá v dokumentaci k Visual C++. Běžné knihovny DLL MFC, který je staticky propojené do MFC má stejné vlastnosti jako dosavadní USRDLL.  


## <a name="mfc_prohibited_classes"></a> Máte nějaká MFC – třídy nebo funkce, které nelze použít v knihovně MFC DLL?
Použití knihoven DLL rozšíření `CWinApp`-odvozené třídy klientské aplikace. Nesmí mít svou vlastní `CWinApp`-odvozené třídy.  
  
Regulární knihovny MFC DLL musí mít `CWinApp`-odvozené třídy a jeden objekt třídy aplikace, stejně jako aplikace knihovny MFC. Na rozdíl od `CWinApp` objekt aplikace, `CWinApp` objekt knihovny DLL nemá hlavní zprávy odeslané.  
  
 Všimněte si, že `CWinApp::Run` mechanismus se nevztahuje na knihovnu DLL, aplikace vlastní hlavní message pump. Pokud knihovnu DLL otevře nemodální dialogová okna nebo má své vlastní okno hlavního rámce, čerpadlo hlavní zpráv aplikace musí volat rutinu exportované sadou knihovnu DLL, která volá `CWinApp::PreTranslateMessage` členské funkce objektu aplikace knihovnu DLL.  

## <a name="mfc_optimization"></a> Jaké optimalizační techniky mám použít ke zlepšení klientská aplikace&#39;s výkon při načítání?
Pokud vaše knihovna DLL je regulární MFC DLL, která je staticky propojené do MFC, změna na běžný MFC DLL dynamicky propojené s knihovnou MFC snižuje velikost souboru.  
  
 Pokud má velký počet exportovaných funkcí knihovna DLL, použijte soubor .def export funkcí (místo použití **__declspec(dllexport)**) a pomocí souborů .def [NONAME – atribut](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) na každém exportované funkce. Atribut NONAME způsobí, že pořadové číslo a ne název funkce má být uložen v knihovně DLL export tabulky a který snižuje velikost souboru.  
  
 Knihovny DLL, které jsou implicitně propojeny s aplikací se načtou při načtení aplikace. Chcete-li zlepšit výkon při načítání, zkuste rozdělit do různých knihoven DLL knihovnu DLL. Uveďte všechny funkce, které je volající aplikace potřebuje ihned po načtení do jedné knihovny DLL a mít volající aplikace implicitně odkaz na tuto knihovnu DLL. Další funkce, které je volající aplikace hned nemusí vložit do jiné knihovny DLL a mít aplikace explicitně odkaz na tuto knihovnu DLL. Další informace najdete v tématu [rozhodování o způsobu vytváření použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).  

## <a name="memory_leak"></a> Existuje&#39;s nevrácenou pamětí v mé běžné knihovny MFC DLL, ale vlastního kódu vypadá dobře. Jak můžete najít nevrácená paměť systému?  
  
Možnou příčinou nevrácené paměti je, že MFC vytvoří dočasné objekty, které se používají v rámci funkce obslužných rutin zpráv. V aplikacích MFC tyto dočasné objekty jsou automaticky vyčištěna v `CWinApp::OnIdle()` funkci, která je volána mezi zpracování zpráv. V MFC dynamické knihovny (DLL), ale `OnIdle()` funkce není volána automaticky. V důsledku toho dočasné objekty nejsou vyčistit automaticky. Vyčistěte dočasné objekty, musí explicitně volání knihovny DLL `OnIdle(1)` pravidelně.  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)