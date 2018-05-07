---
title: Platform::GUID – hodnotová třída | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c295138d6239ce516b4f322fb5fc479e2235a6be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformguid-value-class"></a>Platform::Guid – hodnotová třída
Představuje [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) typu v prostředí Windows Runtime typ systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public value struct Guid  
```  
  
### <a name="members"></a>Členové  
 GUID má Equals(), GetHashCode(), a metody ToString() odvozené z [Platform::Object třída](../cppcx/platform-object-class.md), a metodu GetTypeCode() odvozené z [Platform::Type – třída](../cppcx/platform-type-class.md). Identifikátor GUID má také následující členy.  
  
|Člen|Popis|  
|------------|-----------------|  
|[Identifikátor GUID](#ctor)|Inicializuje novou instanci třídy struktura identifikátor Guid.|  
|[operator==](#operator-equality)|Operátor je rovno.|  
|[operator!=](#operator-not-equal)|Operátor není rovno.|  
|[Operator() –](#operator-call)|Identifikátor Guid převede na identifikátor GUID.|  
  
### <a name="remarks"></a>Poznámky  
 Příklad toho, jak vygenerovat nový Platform::Guid pomocí funkce systému Windows [funkci CoCreateGuid](http://msdn.microsoft.com/library/windows/desktop/ms688568\(v=vs.85\).aspx), najdete v části [součást WinRT: jak vygenerovat identifikátor GUID?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

 
## <a name="ctor"></a> GUID::GUID konstruktory
Inicializuje novou instanci struktury identifikátor Guid.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  );  
  
    Guid(GUID m);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n );  
```  
  
### <a name="parameters"></a>Parametry  
 `a`  
 První 4 bajty identifikátor GUID.  
  
 `b`  
 Další 2 bajty identifikátoru GUID.  
  
 `c`  
 Další 2 bajty identifikátoru GUID.  
  
 `d`  
 Další bajt identifikátoru GUID.  
  
 `e`  
 Další bajt identifikátoru GUID.  
  
 `f`  
 Další bajt identifikátoru GUID.  
  
 `g`  
 Další bajt identifikátoru GUID.  
  
 `h`  
 Další bajt identifikátoru GUID.  
  
 `i`  
 Další bajt identifikátoru GUID.  
  
 `j`  
 Další bajt identifikátoru GUID.  
  
 `k`  
 Další bajt identifikátoru GUID.  
  
 `m`  
 Identifikátor GUID, jak jsou definovány.  
  
 `n`  
 Zbývající 8 bajtů identifikátor GUID.  
  

## <a name="operator-equality"></a> GUID::Operator == – operátor
Porovná dva identifikátory GUID.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::Guid::operator==  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud jsou dva identifikátory GUID stejné.

## <a name="operator-inequality"></a> GUID::Operator! = – operátor
Porovná dva identifikátory GUID.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::Guid::operator!=  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud dva identifikátory GUID nejsou stejné.



## <a name="operator-call"></a> GUID::Operator() – operátor
Implicitně převede [GUID struktura](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)GUID do Platform::Guid.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::Guid operator()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Struktura identifikátor Guid.  
  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)