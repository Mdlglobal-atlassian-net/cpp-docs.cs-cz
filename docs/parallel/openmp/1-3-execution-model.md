---
title: 1.3 Model spouštění | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85ae8bc4-5bf0-45e0-a45f-02de9adaf716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0acdd7a5d9f2dcb58850254281b5c18fd0d1123c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687891"
---
# <a name="13-execution-model"></a>1.3 Model spouštění
OpenMP používá model připojení k rozvětvení paralelní provádění. I když tento model rozvětvení připojení může být užitečná pro řešení různé problémy, poněkud přizpůsobit pro velké aplikace založené na pole. OpenMP je určený pro podporu programy, které budou spuštěny správně i jako paralelní programy (více vláken provádění a knihovnu úplnou podporu OpenMP) a jako sekvenční programy (direktivy ignorována a jednoduchý knihovny zástupných procedur OpenMP). Ale je možné a umožnit vyvíjet program, který není chovat správně při spuštění postupně. Navíc různé stupně paralelního zpracování může vést k jiné číselných výsledků z důvodu změn v association číselné operací. Snížení sériové přidání například může mít jiný vzor přidružení přidání než paralelní snížení. Tyto jiné přidružení může změnit výsledky přidání s plovoucí desetinnou čárkou.  
  
 Program vytvořený pomocí rozhraní API jazyka C/C++ OpenMP zahájí provádění jako jedním vláknem a provádění volat *hlavní vlákno*. Hlavní vlákno spustí sériové oblast až do první paralelní konstrukce. V rozhraní API jazyka C/C++ OpenMP **paralelní** směrnice představuje paralelní konstrukce. Když je zjištěna paralelní konstrukce, hlavní vlákno vytvoří tým vláken a se stává hlavní týmu. Každé vlákno v týmu provede příkazy na dynamické rozsah paralelní oblasti, s výjimkou konstrukce pro sdílení práce. Konstrukce pro sdílení práce musí být zjištěny všechny vlákna v týmu ve stejném pořadí a příkazy v přidružené strukturovaných bloku jsou spouštěny jedním nebo více vláken. Barrier implicitní na konci konstrukt sdílení práce bez `nowait` klauzule je provedený všechna vlákna v týmu.  
  
 Pokud vlákno upraví objekt sdílené, ovlivňuje pouze svou vlastní prostředí pro spuštění, ale také těch, které používá jiná vlákna v programu. Úpravy není zaručena bezpečnost pro dokončení, z hlediska jednoho jiná vlákna na další bod pořadí (podle definice v základním jazyku) pouze v případě, že objekt je deklarován jako volatile. Jinak hodnota úpravy představuje záruku dokončení po první úprava přístup z více vláken, a pak (nebo souběžně) jiná vlákna, dojde **vyprázdnění** direktiva, která určuje objekt (implicitně nebo explicitně). Všimněte si, že pokud **vyprázdnění** direktivy, které jsou implicitní jiné směrnice OpenMP nejsou dostatečná k zajištění požadované řazení vedlejší účinky, je pro programátory odpovědnost k poskytování dalších, explicitní  **vyprázdnění** direktivy.  
  
 Po dokončení paralelní konstrukce vláken v týmu synchronizovat v implicitní bariéry a pouze hlavní vlákno pokračuje v provádění. V jednom programu můžete zadat libovolný počet paralelní konstrukce. V důsledku toho může program rozvětvovat a připojení tolikrát, kolikrát během provádění.  
  
 Rozhraní API jazyka C/C++ OpenMP umožňuje programátorům použít direktivy ve funkcích volat v rámci paralelní konstrukce. Direktivy jazyka, které se nezobrazí v lexikální rozsah paralelní konstrukce, ale může být v dynamické rozsah se nazývají *osamocené* direktivy. Osamocené direktivy poskytne programátorům spouštění hlavní části jejich programu paralelně s jen minimální změny sekvenční programu. Pomocí této funkce můžete uživatelům code paralelní konstrukce na nejvyšší úrovni stromu program volání a použít direktivy k řízení provádění v žádném volaných funkcí.  
  
 Nesynchronizované volání pro C a C++ výstupu funkce, které zapisovat do stejného souboru může být výstup, ve kterém se zobrazí data zapsaná pomocí různých vláknech v nedeterministická pořadí. Podobně nesynchronizovaných volání jako vstup funkce, které čtou ze stejného souboru může číst data v pořadí nedeterministická. Nesynchronizované použití vstupně-výstupních operací, tak, aby každé vlákno používá jiný soubor, vytvoří stejné výsledky jako sériové provádění funkcí vstupně-výstupní operace.