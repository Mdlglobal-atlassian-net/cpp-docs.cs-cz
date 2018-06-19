---
title: Použití příkazu VERIFY místo ASSERT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- assert
dev_langs:
- C++
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 712c22bec1d6ce2d67208de9a139dff7621ad4cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376556"
---
# <a name="using-verify-instead-of-assert"></a>Použití příkazu VERIFY místo ASSERT
Předpokládejme, že při spuštění ladicí verzi vaší aplikace knihovny MFC neexistují žádné problémy. Prodejní verze stejné aplikace však dojde k chybě, vrátí nesprávné výsledky nebo vykazuje některé neobvyklé chování.  
  
 Tento problém může být způsobeno při umístění důležité kódu v příkazu ASSERT k ověření, které provádí správně. Protože ASSERT – příkazy jsou komentované v sestavení pro vydání programu MFC, kód se nespouští v sestavení pro vydání.  
  
 Pokud používáte ASSERT potvrďte, že volání funkce proběhlo úspěšně, zvažte použití [OVĚŘTE](../../mfc/reference/diagnostic-services.md#verify) místo. Makro OVĚŘTE vyhodnotí vlastní argumenty v obou ladění a vydání sestavení aplikace.  
  
 Jiné upřednostňovaná technika je dočasný proměnné přiřadit návratovou hodnotu funkce a otestujte proměnné v příkazu ASSERT.  
  
 Zkontrolujte následující fragment kódu:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 Tento kód spustí perfektně v ladicí verze aplikace knihovny MFC. Pokud volání `calloc( )` selže, diagnostiky zprávu, která obsahuje soubor a řádku číslo se zobrazí. Ale v prodejní sestavení aplikace MFC:  
  
-   volání `calloc( )` nikdy neprovádí, ponechat `buf` neinicializovaný, nebo  
  
-   `strcpy_s( )` kopie "`Hello, World`" do náhodných část paměti, může být selhání aplikace nebo způsobuje systém přestane reagovat, nebo  
  
-   `free()` pokusí se volné paměti, který se nikdy přidělen.  
  
 Pokud chcete používat ASSERT správně, by mělo být změněno ukázka kódu takto:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );  
ASSERT( buf != NULL );  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 Nebo můžete místo toho použít OVĚŘTE:  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
## <a name="see-also"></a>Viz také  
 [Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)