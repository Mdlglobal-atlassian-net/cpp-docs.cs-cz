---
title: "set_unexpected – (CRT) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: set_unexpected
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords: set_unexpected
dev_langs: C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2798fff46d40ed6100f101cbc8839ad2fd166f4b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)
Nainstaluje ukončení funkce má být volána `unexpected`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unexpected_function set_unexpected(  
   unexpected_function unexpFunction   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `unexpFunction`  
 Ukazatel na funkci, která můžete psát nahradit `unexpected` funkce.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel na funkci předchozí ukončení registrovaných `_set_unexpected` , aby předchozí funkce můžete později obnovit. Pokud byla nastavena žádná předchozí funkce, návratovou hodnotu může použít k obnovení výchozího chování; Tato hodnota může mít hodnotu NULL.  
  
## <a name="remarks"></a>Poznámky  
 `set_unexpected` Funkce nainstaluje `unexpFunction` jako funkce volá `unexpected`. `unexpected`nepoužívá se v aktuální implementace zpracování výjimek C++. `unexpected_function` Typ je definována v EH. H jako ukazatel na uživatelem definované neočekávaná funkce `unexpFunction` , který vrací `void`. Vaše vlastní `unexpFunction` funkce by neměla vrátit do jeho volajícího.  
  
```  
typedef void ( *unexpected_function )( );  
```  
  
 Ve výchozím nastavení `unexpected` volání `terminate`. Toto výchozí chování můžete změnit tak, že zápis ukončení funkce a volání `set_unexpected` s názvem funkce jako její argument. `unexpected`volá funkci naposledy zadaný jako argument pro `set_unexpected`.  
  
 Na rozdíl od nainstalované ve volání funkce vlastní ukončení `set_terminate`, můžete v rámci vyvolána výjimka `unexpFunction`.  
  
 V prostředí s více vlákny neočekávané funkce jsou pro každé vlákno udržovány odděleně. Každé vlákno je potřeba nainstalovat vlastní neočekávaná funkce. Proto každé vlákno má na starosti vlastní neočekávané zpracování.  
  
 Zpracovávání výjimek v jazyce C++, aktuální implementace Microsoft `unexpected` volání `terminate` ve výchozím nastavení a nikdy volá knihovna RTL – zpracování výjimek. Neexistuje žádné konkrétní výhody volání `unexpected` místo `terminate`.  
  
 Na jeden `set_unexpected` obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo exe soubory; i v případě, že zavoláte `set_unexpected` vaší obslužné rutiny, může být nahrazen jiným nebo nahrazujete obslužnou rutinu DLL nebo EXE nastavit jiný.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`set_unexpected`|\<EH.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [_get_unexpected –](../../c-runtime-library/reference/get-unexpected.md)   
 [set_terminate –](../../c-runtime-library/reference/set-terminate-crt.md)   
 [ukončení](../../c-runtime-library/reference/terminate-crt.md)   
 [neočekávané](../../c-runtime-library/reference/unexpected-crt.md)