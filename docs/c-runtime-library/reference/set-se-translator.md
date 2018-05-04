---
title: _set_se_translator – | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d4a5c9e86023ea47f23b648cad1a4dffedf905b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="setsetranslator"></a>_set_se_translator

Nastavte funkci zpětného volání vlákno přeložit Win32 výjimek (C strukturovaná výjimky) do C++ zadali výjimky.

## <a name="syntax"></a>Syntaxe

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parametry

*seTransFunction*<br/>
Ukazatel na a C strukturovaná funkce překladač výjimka, která můžete zapsat.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na funkci předchozí překladač registrovaných **_set_se_translator –**tak, aby předchozí funkce může být obnovena novější. Pokud byla nastavena žádná předchozí funkce, návratovou hodnotu lze použít k obnovení výchozího chování; Tato hodnota může být **nullptr**.

## <a name="remarks"></a>Poznámky

**_Set_se_translator –** funkce poskytuje způsob, jak zpracování Win32 výjimek (C strukturovaná výjimky) jako C++ zadali výjimky. Povolit jednotlivých výjimkách C C++ zpracovávat **catch** obslužnou rutinu, nejprve definice třídy obálku C výjimka, která lze použít, nebo odvozené od, do atribut typu určité třídy C výjimka. Pokud chcete používat tuto třídu, nainstalujte vlastní funkce překladač výjimka C, která je volána metodou interní mechanismus zpracování výjimek pokaždé, když je vyvolána výjimka C. V rámci funkce překladač, můžete vyvolat žádné typu výjimka, která může být zachycen odpovídající C++ **catch** obslužné rutiny.

Je nutné použít [/EHa](../../build/reference/eh-exception-handling-model.md) při použití **_set_se_translator –**.

Chcete-li zadat vlastní překlad funkce, volejte **_set_se_translator –** pomocí názvu funkce překladu jako její argument. Překladač funkce, která můžete psát nazývá jednou pro každé vyvolání funkce v zásobníku, která má **zkuste** bloky. Neexistuje žádný výchozí překladač funkce.

Překladač funkce měli dělat žádné další než throw jazyka C++ zadali výjimka. Pokud k tomu nic kromě vyvolání (například zápis do souboru protokolu, například) vašeho programu nemusí chovat podle očekávání, protože počet, kolikrát je volána funkce překladač je závislá na platformu.

V prostředí s více vlákny jsou funkce překladač udržovány odděleně pro každé vlákno. Každé vlákno je potřeba nainstalovat funkci vlastní překladač. Proto každé vlákno má na starosti vlastní zpracování překlad. **_set_se_translator –** je specifická pro jedno vlákno; jiné knihovny DLL může nainstalovat funkci různých překlad.

*SeTransFunction* funkce, které můžete psát musí být zkompilovány nativní funkce (není kompilovat s volbou/CLR). Celé číslo bez znaménka a ukazatel musí provést na Win32 **_exception_pointers –** struktury jako argumenty. Argumenty jsou vrácené hodnoty volání do rozhraní API Win32 **GetExceptionCode –** a **GetExceptionInformation** funguje, v uvedeném pořadí.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Pro **_set_se_translator –**, jsou dopady při dynamicky propojení s CRT; jiné může volání knihovny DLL v procesu **_set_se_translator –** a nahraďte vaší obslužné rutiny vlastní.

Při použití **_set_se_translator –** ze spravovaného kódu (kód kompilovat s volbou/CLR) nebo ve smíšeném nativního a spravovaného kódu, uvědomte si, že překladač ovlivňuje výjimky vygenerované v nativním kódu jenom. Některé spravované výjimky generované ve spravovaném kódu (například při vyvolání `System::Exception`) nejsou směrovány prostřednictvím funkce překladač. Výjimek vyvolaných ve spravovaném kódu pomocí funkce Win32 **raiseexception –** nebo způsobeno výjimkou systému, jako jsou Rozděl nulové výjimkou jsou směrovány prostřednictvím překladač.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class SE_Exception
{
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception( unsigned int n ) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func(unsigned int u, EXCEPTION_POINTERS*)
{
    throw SE_Exception(u);
}

int main()
{
    auto original = _set_se_translator(trans_func);
    try
    {
        SEFunc();
    }
    catch(SE_Exception& e)
    {
        printf("Caught a __try exception, error %8.8x.\n", e.getSeNumber());
    }
    _set_se_translator(original);
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Příklad

I když funkce poskytované **_set_se_translator –** je ve spravovaném kódu není k dispozici, je možné použít mapování v nativním kódu i v případě, že nativního kódu je v kompilaci v části **/CLR** přepínače, nativní kód je uveden pomocí `#pragma unmanaged`. Pokud strukturovaného výjimek je hlášeny ve spravovaném kódu, který se má namapovat, musí být označen kód, který generuje a ošetří výjimku `#pragma unmanaged`. Následující kód ukazuje možné použít. Další informace najdete v tématu [direktivy Pragma a klíčové slovo __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class CMyException{
private:
    unsigned int nSE;
public:
    CMyException() : nSE{ 0 } {}
    CMyException(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw CMyException(u);
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

int main() {
    auto original = _set_se_translator(my_trans_func);
    DoTest();
    _set_se_translator(original);
}
```

```Output
Caught CMyException, error c0000094
```

## <a name="see-also"></a>Viz také

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Ukončení](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
