---
title: "set_terminate – (CRT) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords: set_terminate
dev_langs: C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 099cb340f821f04c3a5f84ccef7e3e9649482cd6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setterminate-crt"></a>set_terminate (CRT)
Nainstaluje vlastní rutiny ukončení má být volána `terminate`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `termFunction`  
 Ukazatel na funkci ukončit, která můžete zapsat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na funkci předchozí registrovaných `set_terminate` , aby předchozí funkce můžete později obnovit. Pokud byla nastavena žádná předchozí funkce, návratovou hodnotu může použít k obnovení výchozího chování; Tato hodnota může mít hodnotu NULL.  
  
## <a name="remarks"></a>Poznámky  
 `set_terminate` Funkce nainstaluje `termFunction` jako funkce volá `terminate`. `set_terminate`se používá s zpracovávání výjimek v jazyce C++ a může být volána v libovolném bodě v programu, než je vyvolána výjimka. `terminate`volání `abort` ve výchozím nastavení. Toto výchozí nastavení můžete změnit tak, že zápis ukončení funkce a volání `set_terminate` s názvem funkce jako její argument. `terminate`volá funkci naposledy zadaný jako argument pro `set_terminate`. Po provedení všechny potřeby úlohy čištění, `termFunction` programu musí ukončit. Pokud neexistuje (Pokud se vrátí do jeho volajícího), `abort` je volána.  
  
 V prostředí s více vlákny ukončit funkce jsou udržovány odděleně pro každé vlákno. Každé vlákno je potřeba nainstalovat svou vlastní funkci ukončit. Proto každé vlákno má na starosti vlastní zpracování ukončení.  
  
 `terminate_function` Typ je definována v EH. H jako ukazatel na funkci ukončení definovaný uživatelem, `termFunction` , který vrací `void`. Vaše vlastní funkce `termFunction` můžete nepřebírají žádné argumenty a by neměla vrátit do jeho volajícího. Pokud ano, `abort` je volána. Nemusí být vyvolána výjimka uvnitř `termFunction`.  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  `set_terminate` Funkce funguje pouze mimo ladicí program.  
  
 Na jeden `set_terminate` obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo exe soubory; i v případě, že zavoláte `set_terminate` vaší obslužné rutiny, může být nahrazen jiným, nebo může být nahrazení obslužnou rutinu nastavit jiný knihovny DLL nebo EXE.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`set_terminate`|\<EH.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [ukončit](../../c-runtime-library/reference/terminate-crt.md).  
  
## <a name="see-also"></a>Viz také  
 [Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [_get_terminate –](../../c-runtime-library/reference/get-terminate.md)   
 [set_unexpected –](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [ukončení](../../c-runtime-library/reference/terminate-crt.md)   
 [neočekávané](../../c-runtime-library/reference/unexpected-crt.md)