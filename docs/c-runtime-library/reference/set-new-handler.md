---
title: "_set_new_handler – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_new_handler
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
f1_keywords:
- _set_new_handler
- set_new_handler
dev_langs: C++
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ab5d0da21b7034d1a5ab336854b87ae2d2cc429
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setnewhandler"></a>_set_new_handler
Přenosy ovládacího prvku na váš mechanismus zpracování chyb, pokud `new` operátor se nepodařilo přidělit paměť.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_PNH _set_new_handler(  
   _PNH pNewHandler   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pNewHandler`  
 Ukazatel na zpracování funkce paměti zadané aplikace. Argument 0 způsobí, že novou obslužnou rutinu odeberou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na předchozí výjimku zpracování funkce registrovaných `_set_new_handler`tak, aby předchozí funkce může být obnovena novější. Pokud byla nastavena žádná předchozí funkce, návratovou hodnotu lze použít k obnovení výchozího chování; Tato hodnota může být `NULL`.  
  
## <a name="remarks"></a>Poznámky  
 C++ `_set_new_handler` funkce určuje funkci zpracování výjimek, získá kontrolu, pokud `new` operátor se nepodařilo přidělit paměť. Pokud `new` selže, spuštění systému automaticky volá funkci zpracování výjimek, který byl předán jako argument pro `_set_new_handler`. `_PNH`, definuje New.h, je zde ukazatel na funkci, která vrátí typ `int` a trvá argument typu `size_t`. Použití `size_t` k určení množství místa, která bude přidělena.  
  
 Neexistuje žádný výchozí obslužnou rutinu.  
  
 `_set_new_handler`je v podstatě schéma kolekce paměti. Běhu systému opakuje přidělení pokaždé, když funkce vrátí nenulovou hodnotu, se nezdaří, pokud funkce vrátí hodnotu 0.  
  
 Výskyt `_set_new_handler` funkce v programu zaregistruje funkci zpracování výjimek, který je uvedený v seznamu argument s běhu systému:  
  
```  
#include <new.h>  
int handle_program_memory_depletion( size_t )  
{  
   // Your code  
}  
int main( void )  
{  
   _set_new_handler( handle_program_memory_depletion );  
   int *pi = new int[BIG_NUMBER];  
}  
```  
  
 Můžete uložit adresu funkce, která naposledy byl předán `_set_new_handler` funkce a obnovte ji později:  
  
```  
_PNH old_handler = _set_new_handler( my_handler );  
   // Code that requires my_handler  
   _set_new_handler( old_handler )  
   // Code that requires old_handler  
```  
  
 C++ [_set_new_mode –](../../c-runtime-library/reference/set-new-mode.md) funkce nastaví nový režim obslužné rutiny pro [malloc –](../../c-runtime-library/reference/malloc.md). Nový režim obslužná rutina označuje, jestli při selhání, `malloc` je volat nové rutiny obslužných rutin jako sady pomocí `_set_new_handler`. Ve výchozím nastavení `malloc` nevyvolá nové rutiny ovladače při selhání při přidělování paměti. Toto výchozí chování můžete přepsat tak, aby, když `malloc` nepodaří přidělit paměť, `malloc` volání nové rutiny obslužná rutina ve stejné způsobem, jako `new` operátor nepodporuje, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí nastavení, zavolejte:  
  
```  
_set_new_mode(1)  
```  
  
 časná v vašeho programu nebo odkaz s Newmode.obj.  
  
 Pokud uživatelem definované `operator new` je k dispozici nové funkce obslužných rutin nejsou automaticky volána při selhání.  
  
 Další informace najdete v tématu [nové](../../cpp/new-operator-cpp.md) a [odstranit](../../cpp/delete-operator-cpp.md) v *referenční příručka jazyka C++*.  
  
 Na jeden `_set_new_handler` obslužné rutiny pro všechny dynamicky propojené knihovny DLL nebo spustitelné soubory; i v případě, že zavoláte `_set_new_handler` vaší obslužné rutiny může být nahrazena jinou nebo nahrazujete obslužnou rutinu nastavit jiný knihovny DLL nebo spustitelný soubor.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_set_new_handler`|\<New.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu při přidělení nezdaří, je ovládací prvek přenesen na MyNewHandler. Argument předaný MyNewHandler je počet bajtů. Hodnota vrácená z MyNewHandler je příznak označující, zda je třeba opakovat přidělení: nenulovou hodnotu označuje, že je třeba opakovat přidělení a nulová hodnota znamená, že přidělení selhala.  
  
```  
// crt_set_new_handler.cpp  
// compile with: /c  
#include <stdio.h>  
#include <new.h>  
#define BIG_NUMBER 0x1fffffff  
  
int coalesced = 0;  
  
int CoalesceHeap()  
{  
   coalesced = 1;  // Flag RecurseAlloc to stop   
   // do some work to free memory  
   return 0;  
}  
// Define a function to be called if new fails to allocate memory.  
int MyNewHandler( size_t size )  
{  
   printf("Allocation failed. Coalescing heap.\n");  
  
   // Call a function to recover some heap space.  
   return CoalesceHeap();  
}  
  
int RecurseAlloc() {  
   int *pi = new int[BIG_NUMBER];  
   if (!coalesced)  
      RecurseAlloc();  
   return 0;  
}  
  
int main()  
{  
   // Set the failure handler for new to be MyNewHandler.  
   _set_new_handler( MyNewHandler );  
   RecurseAlloc();  
}  
```  
  
```Output  
Allocation failed. Coalescing heap.  
  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)