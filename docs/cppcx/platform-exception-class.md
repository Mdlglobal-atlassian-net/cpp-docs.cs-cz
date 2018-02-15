---
title: "Třída Platform::Exception | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51df721524fa871b28cc7e4bcb088d4a82a0d1ad
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformexception-class"></a>Platform::Exception – třída
Reprezentuje chyby, ke kterým došlo během provádění aplikací. Třídy výjimek vlastní nemůže být odvozen od `Platform::Exception`. Pokud budete potřebovat vlastní výjimky, můžete použít `Platform::COMException` a zadejte HRESULT konkrétní aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class Exception : Object,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>Členové  
 `Exception` Třída dědí z `Object` třídy a `IException`, `IPrintable`, a `IEquatable` rozhraní.  
  
 `Exception` Třída také obsahuje následující typy členů.  
  
### <a name="constructors"></a>Konstruktory  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::Exception](#ctor)|Inicializuje novou instanci třídy `Exception` třídy.|  
  
### <a name="methods"></a>Metody  
 `Exception` Třída dědí `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`, a `ToString()` metody z [Platform::Object třída](../cppcx/platform-object-class.md). `Exception` Třída také obsahuje následující metodu.  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::CreateException](#createexception)|Vytvoří výjimku, která představuje zadaná hodnota HRESULT.|  
  
### <a name="properties"></a>Vlastnosti  
 Třídy výjimek také má následující vlastnosti.  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::HResult](#hresult)|HRESULT, která odpovídá výjimku.|  
|[Exception::Message](#message)|Zpráva popisující výjimku Tato hodnota je jen pro čtení a nejde změnit `Exception` je vytvořený.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

## <a name="createexception"></a> Exception::CreateException – metoda
Vytvoří Platform::Exception ^ z zadanou hodnotou HRESULT.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Exception^ CreateException(int32 hr)  
Exception^ CreateException(int32 hr, Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parametry  
 personální oddělení  
 Hodnota HRESULT, který obvykle získat z volání metody COM. Pokud je hodnota 0, která je rovna S_OK, tato metoda vyvolá [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) protože metody modelu COM, které úspěšné nesmí generování výjimek.  
  
 – zpráva  
 Řetězec, který popisuje danou chybu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výjimka, která představuje chybu HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k vytvoření výjimku mimo HRESULT, která je vrácena, například volání metody rozhraní COM. Můžete použít přetížení, která přebírá řetězec ^ parametr zadejte vlastní zprávu.  
  
 Je důrazně doporučené vytvořit výjimka silného typu pomocí CreateException místo vytváření [Platform::COMException](../cppcx/platform-comexception-class.md) obsahující jenom hodnota HRESULT.  
  


## <a name="ctor"></a>  Exception::Exception – konstruktor
Intializes novou instanci třídy výjimek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
Exception(int32 hresult)  
Exception(int32 hresult, ::Platform::String^ message)  
```  
  
### <a name="parameters"></a>Parametry  
 `hresult`  
 Chyba HRESULT, která je reprezentována výjimku.  
  
 `message`  
 Zpráva definované uživatelem, jako je například doporučený text, který je přidružen výjimku. Obecně by měla přednost druhý přetížení Chcete-li zadat popisný zprávu, která je co možná o tom, jak a proč došlo k chybě.  
  


## <a name="hresult"></a>  Vlastnost Exception::HResult
HRESULT, která odpovídá výjimku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 Hodnotou HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Většina výjimek spustí jako chyby COM, které se vrátí jako HRESULT hodnoty. C + +/ CX převede tyto hodnoty Platform::Exception ^ objektů a tuto vlastnost ukládá hodnotu identifikátoru původní kód chyby.  
  


## <a name="message"></a> Vlastnost Exception::Message
Zpráva, která popisuje danou chybu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property String^ Message;  
```  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 V výjimky, které pocházejí z prostředí Windows Runtime je to poskytnuté systémem popis chyby.  
  
### <a name="remarks"></a>Poznámky  
 V systému Windows 8 Tato vlastnost je jen pro čtení protože výjimky v této verzi prostředí Windows Runtime jsou přenosu mezi ABI pouze jako hodnoty HRESULT. Ve Windows 8.1 bohatší informace o výjimce se přenášejí mezi ABI a může poskytnout vlastní zprávu, ostatní součásti může přistupovat prostřednictvím kódu programu. Další informace najdete v tématu [výjimek (C + +/ CX)](../cppcx/exceptions-c-cx.md).  
  

  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)