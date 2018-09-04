---
title: Platform::COMException – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
dev_langs:
- C++
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef60fc542b38c7619ce7b65cc7f39db79ed1b228
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679021"
---
# <a name="platformcomexception-class"></a>Platform::COMException – třída
Reprezentuje chyby modelu COM., ke kterým dochází při spuštění aplikace. COMException je základní třídou pro sadu předdefinovaných, standardní výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>Členové  
 COMException – třída dědí z třídy objektu a IException IPrintable a IEquatable rozhraní.  
  
 COMException má také následující typy členů.  
  
 **Konstruktory**  
  
|Člen|Popis|  
|------------|-----------------|  
|[COMException](#ctor)|Inicializuje novou instanci třídy COMException.|  
  
 **Metody**  
  
 COMException – třída dědí metody Equals() Finalize(), GetHashCode(), GetType(), MemberwiseClose() a ToString() z [Platform::Object – třída](../cppcx/platform-object-class.md).  
  
 **Vlastnosti**  
  
 COMException – třída má následující vlastnosti.  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::HResult](#hresult)|Hodnota HRESULT, která odpovídá na výjimku.|  
|[Exception::Message](#message)|Zpráva popisující výjimku.|  
  
## <a name="derived-exceptions"></a>Odvozené výjimky  
 Následující předdefinované výjimky jsou odvozeny z COMException. Se liší od COMException pouze v jejich název, název jejich konstruktoru a jejich základní hodnotu HRESULT.  
  
|Název|Základní hodnota HRESULT|Popis|  
|----------|------------------------|-----------------|  
|COMException|*uživatelem definované hresult*|Vyvolána, když je nerozpoznaný HRESULT vrácená z volání metody COM.|  
|AccessDeniedException|E_ACCESSDENIED|Vyvolána, když byl odepřen přístup k prostředku nebo funkce.|  
|ChangedStateException|E_CHANGED_STATE|Vyvolána výjimka při volání metody iterátoru shromažďování nebo zobrazení kolekce po změně kolekce nadřazených, proto už není platná výsledky metody.|  
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Vyvolána, když třída modelu COM není zaregistrovaný.|  
|DisconnectedException|RPC_E_DISCONNECTED|Vyvolána, když je objekt odpojen od svých klientů.|  
|FailureException|E_FAIL|Vyvolána, pokud se operace nezdaří.|  
|InvalidArgumentException|E_INVALIDARG|Vyvolána, když jeden z argumentů, poskytnutý metodě není platný.|  
|InvalidCastException|E_NOINTERFACE|Vyvolána, když typ nelze převést na jiného typu.|  
|NotImplementedException|E_NOTIMPL|Vyvolána, pokud se neimplementoval metodu rozhraní na třídě.|  
|NullReferenceException|E_POINTER|Vyvolána, když je pokus přistoupit přes ukazatel odkaz na objekt s hodnotou null.|  
|OperationCanceledException –|E_ABORT|Vyvolána, pokud je operace přerušena.|  
|OutOfBoundsException|E_BOUNDS|Vyvolána, když se pokusí získat přístup k datům mimo platný rozsah operace.|  
|OutOfMemoryException|E_OUTOFMEMORY|Vyvolána, když není dostatek paměti k dokončení operace.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serverem:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

## <a name="ctor"></a> COMException::COMException konstruktor
Inicializuje novou instanci třídy COMException.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
COMException( int hresult )  
```  
  
### <a name="parameters"></a>Parametry  
 Hodnota HRESULT  
 Chyba HRESULT, která je reprezentována výjimku.  
  


## <a name="hresult"></a> Vlastnost COMException::HResult
Hodnota HRESULT, která odpovídá na výjimku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 Hodnota HRESULT, která určuje chybu.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, jak interpretovat hodnota HRESULT, naleznete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes).  

## <a name="message"></a> Vlastnost COMException::Message
Zpráva popisující výjimku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property String^ Message {    String^ get();}  
```  
  
### <a name="property-value"></a>Hodnota vlastnosti  
 Popis výjimky.  
    

## <a name="see-also"></a>Viz také  
 [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)