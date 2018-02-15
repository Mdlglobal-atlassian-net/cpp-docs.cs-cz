---
title: _set_se_translator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_se_translator
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
f1_keywords:
- _set_se_translator
- set_se_translator
dev_langs:
- C++
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35ceedca9d26b92d96a3796a3deadee5e62f7f02
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="setsetranslator"></a>_set_se_translator
Obslužné rutiny výjimky Win32 (C strukturovaná výjimky) jako C++ zadali výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_se_translator_function _set_se_translator(  
   _se_translator_function seTransFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `seTransFunction`  
 Ukazatel na a C strukturovaná funkce překladač výjimka, která můžete zapsat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel na funkci předchozí překladač registrovaných `_set_se_translator`tak, aby předchozí funkce může být obnovena novější. Pokud byla nastavena žádná předchozí funkce, návratovou hodnotu lze použít k obnovení výchozího chování; Tato hodnota může být NULL.  
  
## <a name="remarks"></a>Poznámky  
 `_set_se_translator` Funkce poskytuje způsob, jak zpracování Win32 výjimek (C strukturovaná výjimky) jako C++ zadali výjimky. Povolit jednotlivých výjimkách C C++ zpracovávat `catch` obslužnou rutinu, nejprve definice třídy obálku C výjimka, která lze použít, nebo odvozené od, do atribut typu určité třídy C výjimka. Pokud chcete používat tuto třídu, nainstalujte vlastní funkce překladač výjimka C, která je volána metodou interní mechanismus zpracování výjimek pokaždé, když je vyvolána výjimka C. V rámci funkce překladač, můžete vyvolat žádné typu výjimka, která může být zachycen odpovídající C++ `catch` obslužné rutiny.  
  
 Je nutné použít [/EHa](../../build/reference/eh-exception-handling-model.md) při použití `_set_se_translator`.  
  
 Chcete-li zadat vlastní překlad funkce, volejte `_set_se_translator` s názvem funkce překladu jako její argument. Překladač funkce, která můžete psát nazývá jednou pro každé vyvolání funkce v zásobníku, která má `try` bloky. Neexistuje žádný výchozí překladač funkce.  
  
 Překladač funkce měli dělat žádné další než throw jazyka C++ zadali výjimka. Pokud k tomu nic kromě vyvolání (například zápis do souboru protokolu, například) vašeho programu nemusí chovat podle očekávání, protože počet, kolikrát je volána funkce překladač je závislá na platformu.  
  
 V prostředí s více vlákny jsou funkce překladač udržovány odděleně pro každé vlákno. Každé vlákno je potřeba nainstalovat funkci vlastní překladač. Proto každé vlákno má na starosti vlastní zpracování překlad. `_set_se_translator` je specifická pro jedno vlákno; jiné knihovny DLL může nainstalovat funkci různých překlad.  
  
 `seTransFunction` Funkce, které můžete psát musí být zkompilovány nativní funkce (není kompilovat s volbou/CLR). Celé číslo bez znaménka a ukazatel musí provést na Win32 `_EXCEPTION_POINTERS` struktury jako argumenty. Argumenty jsou vrácené hodnoty volání do rozhraní API Win32 `GetExceptionCode` a `GetExceptionInformation` funguje, v uvedeném pořadí.  
  
```  
typedef void (*_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );  
```  
  
 Pro `_set_se_translator`, jsou dopady při dynamicky propojení s CRT; jiné může volání knihovny DLL v procesu `_set_se_translator` a nahraďte vaší obslužné rutiny vlastní.  
  
 Při použití `_set_se_translator` ze spravovaného kódu (kód kompilovat s volbou/CLR) nebo ve smíšeném nativního a spravovaného kódu, uvědomte si, že překladač ovlivňuje výjimky vygenerované v nativním kódu jenom. Některé spravované výjimky generované ve spravovaném kódu (například při vyvolání `System::Exception`) nejsou směrovány prostřednictvím funkce překladač. Výjimek vyvolaných ve spravovaném kódu pomocí funkce Win32 `RaiseException` nebo způsobeno výjimkou systému, jako jsou Rozděl nulové výjimkou jsou směrovány prostřednictvím překladač.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_set_se_translator`|\<eh.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_settrans.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
void SEFunc();  
void trans_func( unsigned int, EXCEPTION_POINTERS* );  
  
class SE_Exception  
{  
private:  
    unsigned int nSE;  
public:  
    SE_Exception() {}  
    SE_Exception( unsigned int n ) : nSE( n ) {}  
    ~SE_Exception() {}  
    unsigned int getSeNumber() { return nSE; }  
};  
int main( void )  
{  
    try  
    {  
        _set_se_translator( trans_func );  
        SEFunc();  
    }  
    catch( SE_Exception e )  
    {  
        printf( "Caught a __try exception with SE_Exception.\n" );  
    }  
}  
void SEFunc()  
{  
    __try  
    {  
        int x, y=0;  
        x = 5 / y;  
    }  
    __finally  
    {  
        printf( "In finally\n" );  
    }  
}  
void trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )  
{  
    printf( "In trans_func.\n" );  
    throw SE_Exception();  
}  
```  
  
```Output  
In trans_func.  
In finally  
Caught a __try exception with SE_Exception.  
```  
  
## <a name="example"></a>Příklad  
 I když funkce poskytované `_set_se_translator` je ve spravovaném kódu není k dispozici, je možné použít mapování v nativním kódu i v případě, že nativního kódu je v kompilaci v části `/clr` přepnout, tak dlouho, dokud nativní kód je vytvářen `#pragma unmanaged`. Strukturované výjimek je hlášeny ve spravovaném kódu, který se má namapovat, musí být kód, který generuje a ošetří výjimku označené `pragma`. Následující kód ukazuje možné použít. Další informace najdete v tématu [direktivy Pragma a klíčové slovo __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).  
  
```  
// crt_set_se_translator_clr.cpp  
// compile with: /clr  
#include <windows.h>  
#include <eh.h>  
#include <assert.h>  
#include <stdio.h>  
  
int thrower_func(int i) {  
   int j = i/0;  
  return 0;  
}  
  
class CMyException{  
};  
  
#pragma unmanaged  
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS pExp )  
{  
printf("Translating the structured exception to a C++"  
             " exception.\n");  
throw CMyException();  
}  
  
void DoTest()  
{  
    try  
    {  
      thrower_func(10);  
    }   
  
    catch(CMyException e)  
    {  
printf("Caught CMyException.\n");  
    }  
    catch(...)  
    {  
      printf("Caught unexpected SEH exception.\n");  
    }  
}  
#pragma managed  
  
int main(int argc, char** argv) {  
    _set_se_translator(my_trans_func);  
    DoTest();  
    return 0;  
}  
```  
  
```Output  
Translating the structured exception to a C++ exception.  
Caught CMyException.  
```  
  
## <a name="see-also"></a>Viz také  
 [Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)   
 [set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [Ukončení](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)