---
title: Platform::Exception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
dev_langs:
- C++
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6774aa0d90e9903798cd2a77a480782b669fdc57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586632"
---
# <a name="platformexception-class"></a>Platform::Exception – třída
Reprezentuje chyby, ke kterým dochází při spuštění aplikace. Vlastní výjimky třídy nemůže být odvozen od `Platform::Exception`. Pokud budete potřebovat vlastní výjimky, můžete použít `Platform::COMException` a zadejte HRESULT konkrétní aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class Exception : Object,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>Členové  
 `Exception` Třída dědí z `Object` třídy a `IException`, `IPrintable`, a `IEquatable` rozhraní.  
  
 `Exception` Třída také obsahuje následující druhy členů.  
  
### <a name="constructors"></a>Konstruktory  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::Exception](#ctor)|Inicializuje novou instanci třídy `Exception` třídy.|  
  
### <a name="methods"></a>Metody  
 `Exception` Třída dědí `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`, a `ToString()` metody ze [Platform::Object – třída](../cppcx/platform-object-class.md). `Exception` Třída má také následující metodu.  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::CreateException](#createexception)|Vytvoří výjimku, která představuje zadanou hodnotu HRESULT.|  
  
### <a name="properties"></a>Vlastnosti  
 Třídy výjimek má také následující vlastnosti.  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::HResult](#hresult)|Hodnota HRESULT, která odpovídá na výjimku.|  
|[Exception::Message](#message)|Zpráva popisující výjimku Tato hodnota je jen pro čtení a nelze změnit po `Exception` je vytvořený.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serverem:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

## <a name="createexception"></a> Exception::CreateException – metoda
Vytvoří Platform::Exception ^ ze zadané hodnoty HRESULT.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Exception^ CreateException(int32 hr)  
Exception^ CreateException(int32 hr, Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parametry  
 hr  
 Hodnota HRESULT, která tyto informace obvykle získáte z volání metody COM. Pokud je hodnota 0, což je rovna S_OK, tato metoda vyvolá [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) protože metody modelu COM, které úspěšná by neměla vyvolávat výjimky.  
  
 – zpráva  
 Řetězec popisující chybu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výjimka, která představuje chybu HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete vytvořit výjimka z HRESULT, která je vrácena, například z volání metody COM rozhraní. Můžete použít přetížení, která přebírá řetězec ^ parametr zadejte vlastní zprávu.  
  
 Je důrazně doporučujeme vytvořit výjimku silného typu pomocí CreateException místo vytváření [Platform::COMException –](../cppcx/platform-comexception-class.md) obsahující pouze hodnota HRESULT.  
  


## <a name="ctor"></a>  Exception::Exception konstruktor
Inicializuje novou instanci třídy výjimek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
Exception(int32 hresult)  
Exception(int32 hresult, ::Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parametry  
 `hresult`  
 Chyba HRESULT, která je reprezentována výjimku.  
  
 `message`  
 Zprávy zadané uživatelem, jako je doporučené text, který souvisí s výjimkou. Obecně byste měli dát přednost druhé přetížení negace popisnou zprávou, která je co nejkonkrétnější o tom, jak a proč došlo k chybě.  
  


## <a name="hresult"></a>  Vlastnost Exception::HResult
Hodnota HRESULT, která odpovídá na výjimku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 Hodnotu HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Většina výjimek začíná jako chyby modelu COM, které jsou následně vráceny jako hodnoty HRESULT. C + +/ CX převede tyto hodnoty na Platform::Exception ^ objekty a tato vlastnost slouží k uložení hodnoty původní kód chyby.  
  


## <a name="message"></a> Vlastnost Exception::Message
Zpráva popisující chybu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property String^ Message;  
```  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 V výjimky vzniklé v modulu Windows Runtime je to poskytnuté systémem popis chyby.  
  
### <a name="remarks"></a>Poznámky  
 V systému Windows 8 Tato vlastnost je jen pro čtení vzhledem k tomu, že jsou napříč ABI pouze jako HRESULTS přenosu výjimek v této verzi systému Windows Runtime. Ve Windows 8.1 bohatší informace o výjimkách přenosu napříč ABI a můžete zadat vlastní zprávu, ke kterému programově přístup jiných komponent. Další informace najdete v tématu [výjimky (C + +/ CX)](../cppcx/exceptions-c-cx.md).  
  

  
## <a name="see-also"></a>Viz také  
 [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)