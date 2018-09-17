---
title: _execute_onexit_table _initialize_onexit_table, _register_onexit_function | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
dev_langs:
- C++
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a54e3e5f5f040c80660bd12e6565cef82d09206
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720951"
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table _initialize_onexit_table, _register_onexit_function
Spravuje rutiny má volat na čas ukončení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _initialize_onexit_table(  
    _onexit_table_t* table  
    );  
  
int _register_onexit_function(  
    _onexit_table_t* table,  
    _onexit_t        function  
    );  
  
int _execute_onexit_table(  
    _onexit_table_t* table  
    );  
```  
  
#### <a name="parameters"></a>Parametry

*Tabulka*<br/>
[out v] Ukazatel na tabulce onexit – funkce  
  
*– funkce*<br/>
[in] Ukazatel na funkci, kterou chcete přidat do tabulky onexit – funkce  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu 0. V opačném případě vrátí zápornou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce jsou podrobnosti implementace infrastruktury slouží k podpoře modulu runtime jazyka C a neměla být volána přímo z uživatelského kódu. C runtime používá *onexit – funkce tabulky* představující pořadí registrovaných volání funkce `atexit`, `at_quick_exit`, a `_onexit`. Datová struktura onexit – funkce tabulky je podrobnosti neprůhledné implementace modulu C Runtime; může změnit pořadí a význam svých datových členů. Prověřovány by neměl být externím kódu.  
  
 `_initialize_onexit_table` Funkce inicializuje tabulce onexit – funkce na počáteční hodnotu.  Tato funkce musí být volána před tabulce onexit – funkce je předána buď `_register_onexit_function` nebo `_execute_onexit_table`.  
  
 `_register_onexit_function` Funkce připojí funkci na konec tabulky onexit – funkce.  
  
 `_execute_onexit_table` Funkce spustí všechny funkce v tabulce onexit – funkce, vymaže v tabulce a vrátí. Po volání `_execute_onexit_table`, v tabulce je ve stavu není platná; musí být znovu inicializovány voláním `_initialize_onexit_table` předtím, než je znovu použit.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h >|  
  
 `_initialize_onexit_table`, `_register_onexit_function`, A `_execute_onexit_table` funkce jsou specifické pro Microsoft. Informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [AtExit](../c-runtime-library/reference/atexit.md)   
 [ukončit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)