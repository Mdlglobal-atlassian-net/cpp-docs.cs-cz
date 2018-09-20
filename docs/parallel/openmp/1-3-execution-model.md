---
title: 1.3 Model spouštění | Dokumentace Microsoftu
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
ms.openlocfilehash: c284563a47d21abc9a1dacf045238449d64205d5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394007"
---
# <a name="13-execution-model"></a>1.3 Model spouštění

OpenMP – používá model forku spojení paralelní spuštění. I když tento model forku spojení mohou být užitečné pro vyřešení různých problémů, je trochu přizpůsobit pro velké aplikace založené na pole. OpenMP – je určená pro podporu programy, které se spustí správně i jako paralelních programů (více vláken provádění a knihovnu úplná podpora OpenMP) a jako sekvenční programy (direktivy ignorována a jednoduché knihovny zástupné procedury OpenMP). Nicméně je možné a umožnit vývoj program, který se nechová správně při prováděny postupně. Kromě toho různým stupněm paralelizace může způsobit různých číselných výsledků z důvodu změn v přidružení škály číselných operací. Například sériového portu přidání snížení může mít různé vzor přidružení přidání než paralelní redukci. Tyto jiné přidružení může změnit výsledky s plovoucí desetinnou čárkou sčítání.

Program napsané pomocí rozhraní API pro C/C++ OpenMP zahájí provádění spuštění označované jako jedno vlákno *hlavní vlákno*. Hlavní vlákno provádí v oblasti sériového portu, dokud se zjistil první paralelní konstrukce. V rozhraní API OpenMP C/C++ **paralelní** směrnice představuje paralelní konstrukce. Vyskytne paralelní konstrukce hlavní vlákno vytvoří tým vláken a se stává hlavní týmu. Každé vlákno v týmu provede příkazy na dynamický rozsah paralelní oblasti, s výjimkou konstrukce pro sdílení práce. Konstrukce pro sdílení práce musí být dodržováním všech vláken v týmu ve stejném pořadí a příkazy v rámci přidružené strukturovaný blok jsou spouštěny jedním nebo více vláken. Překážkou implicitní na konci konstruktoru work-sharing bez `nowait` klauzule se spouštějí všemi vlákny v týmu.

Pokud vlákno upraví objekt sdílené, ovlivní to pouze svou vlastní spouštěcí prostředí, ale také ty ostatní vlákna v programu. Změna je zaručeno, že na dokončení, z pohledu jednoho z jiných vláken, v dalším bodě pořadí (podle definice v základní jazyk) pouze v případě, že objekt je deklarován jako volatile. V opačném případě úpravy je zaručeně dokončení po první úprava vlákna a poté (nebo souběžně) ostatní vlákna, dojde **vyprázdnění** směrnice, který určuje objekt (implicitně nebo explicitně). Všimněte si, že **vyprázdnění** direktivy, které jsou odvozené od jiné direktivy OpenMP nejsou dostatečná k zajištění požadované řazení vedlejší účinky, zodpovídá programátor slouží k poskytování dalších, explicitní  **vyprázdnění** direktivy.

Po dokončení paralelní konstrukce synchronizaci vláken v týmu na implicitní bariéry a pouze hlavní vlákno pokračuje v provádění kódu. V jediném programu můžete zadat libovolný počet paralelní konstrukce pro. V důsledku toho může program vytvořit fork a připojte se k během provádění v mnoha případech.

Rozhraní API OpenMP – C/C++ umožňuje programátorům ve funkcích volaných z v rámci paralelní konstrukce pro použití direktivy. Direktivy, které se nezobrazí v lexikálním rozsahu paralelní konstrukce ale můžou být v rozsahu dynamické se nazývají *osamocené* direktivy. Osamocené direktivy umožňují programátorům paralelně s pouze minimálním změny do sekvenční program spustit hlavní části tohoto programu. Pomocí této funkce můžete uživatelům kódu paralelní konstrukce v nejvyšší úrovně stromu volání aplikace a použít direktivy k řízení provádění v některém z volané funkce.

Nesynchronizované volání jazyka C a C++ výstupních funkcí, které se zapisovat do stejného souboru může vést k výstupu, ve kterém se zobrazí data napsané v různých vláknech popořadě nedeterministická. Nesynchronizované volání k zadání funkce, které čtou ze stejného souboru obdobně může číst data v nedeterministická pořadí. Nesynchronizované použití vstupně-výstupních operací, tak, aby každé vlákno má přístup k jiný soubor, vytvoří stejné výsledky jako sériové provádění funkcí vstupně-výstupních operací.