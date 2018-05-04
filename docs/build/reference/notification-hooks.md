---
title: Háky oznámení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0210c4ee058694594893a029789442c89003da2e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="notification-hooks"></a>Háky oznámení
Háky oznámení se nazývají těsně před v pomocnou rutinou budou provedeny následující akce:  
  
-   Pokud chcete zobrazit, pokud již byl načten se kontroluje uložené popisovač do knihovny.  
  
-   **LoadLibrary** je volána k pokusu o načtení knihovny DLL.  
  
-   **GetProcAddress** nazývá pokoušet o získání adresy procedury.  
  
-   Vraťte se k převodu zatížení import zpoždění.  
  
 Je povolen hák oznámení:  
  
-   Zadáním novou definici ukazatele **__pfnDliNotifyHook2** , je inicializována tak, aby odkazovalo na vlastní funkce, která bude přijímat oznámení.  
  
     -nebo-  
  
-   Nastavením ukazatele **__pfnDliNotifyHook2** do funkce háku před volání knihovny DLL, která je program zpoždění načítání.  
  
 Pokud se oznámení o **dliStartProcessing**, funkce háku může vrátit:  
  
 NULL  
 Pomocník výchozí zpracovává načítání knihovny DLL. To je užitečné, která se má volat pouze pro informační účely.  
  
 Ukazatel na funkci  
 Nepoužívat zpracování načtení zpoždění výchozí. Díky tomu můžete zadat vlastní obslužnou rutinu zatížení.  
  
 Pokud se oznámení o **dliNotePreLoadLibrary**, funkce háku může vrátit:  
  
-   0, pokud právě chce Informační oznámení.  
  
-   HMODULE pro načtené knihovny DLL, pokud jej načíst knihovnu DLL, sám sebe.  
  
 Pokud se oznámení o **dliNotePreGetProcAddress**, funkce háku může vrátit:  
  
-   0, pokud právě chce Informační oznámení.  
  
-   Pokud funkce háku získá adresu samotné adresa importované funkce.  
  
 Pokud se oznámení o **dliNoteEndProcessing**, funkce háku vrácená hodnota je ignorována.  
  
 Pokud tento ukazatel je inicializována (nenulové hodnoty), bude pomocná zatížení zpoždění vyvolají funkci v určitých bodech oznámení v celé jeho spuštění. Ukazatel na funkci má následující definice:  
  
```  
// The "notify hook" gets called for every call to the  
// delay load helper.  This allows a user to hook every call and  
// skip the delay load helper entirely.  
//  
// dliNotify == {  
//  dliStartProcessing |  
//  dliNotePreLoadLibrary  |  
//  dliNotePreGetProc |  
//  dliNoteEndProcessing}  
//  on this call.  
//  
ExternC  
PfnDliHook   __pfnDliNotifyHook2;  
  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 Předejte oznámení **DelayLoadInfo** Struktura funkce háku spolu s hodnotou oznámení. Tato data se shoduje používaného zpoždění zatížení pomocnou rutinou. Jedna z hodnot fronty definovaných v hodnotě oznámení bude [struktura a definice konstant](../../build/reference/structure-and-constant-definitions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md)