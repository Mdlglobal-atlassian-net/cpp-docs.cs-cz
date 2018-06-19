---
title: Třída Platform::COMException | Microsoft Docs
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79c7824a64fc9bfa4bef761e82505195835146ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090521"
---
# <a name="platformcomexception-class"></a>Platform::COMException – třída
Reprezentuje chyby COM, ke kterým došlo během provádění aplikací. COMException je základní třída pro sadu předdefinovaných, standard výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>Členové  
 COMException – třída dědí z třídy objektu a IException, IPrintable a IEquatable rozhraní.  
  
 COMException má také následující typy členů.  
  
 **Konstruktory**  
  
|Člen|Popis|  
|------------|-----------------|  
|[COMException](#ctor)|Inicializuje novou instanci třídy COMException.|  
  
 **Metody**  
  
 Třída COMException dědí z metody Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() a ToString() [Platform::Object třída](../cppcx/platform-object-class.md).  
  
 **Vlastnosti**  
  
 COMException – třída má následující vlastnosti.  
  
|Člen|Popis|  
|------------|-----------------|  
|[Exception::HResult](#hresult)|HRESULT, která odpovídá výjimku.|  
|[Exception::Message](#message)|Zpráva, která popisuje výjimku.|  
  
## <a name="derived-exceptions"></a>Odvozené výjimky  
 Následující předdefinované výjimky jsou odvozeny od COMException. Se liší od COMException pouze v jména, názvu jejich konstruktor a jejich základní hodnota HRESULT.  
  
|Název|Základní HRESULT|Popis|  
|----------|------------------------|-----------------|  
|COMException|*uživatelem definované hresult*|Vyvolá, když je nerozpoznané HRESULT vrácená z volání metody COM.|  
|AccessDeniedException|E_ACCESSDENIED|Vyvolá, když byl odepřen přístup k prostředku nebo funkce.|  
|ChangedStateException|E_CHANGED_STATE|Vyvolá, když jsou volány metody iterator kolekce nebo kolekce zobrazení po změně její nadřazená kolekce, zneplatnění výsledky metody.|  
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Vyvolá, když třídy COM není zaregistrován.|  
|DisconnectedException|RPC_E_DISCONNECTED|Vyvolá, když je objekt odpojen od jeho klienty.|  
|FailureException|E_FAIL|Vygeneruje se, když se operace nezdaří.|  
|InvalidArgumentException|E_INVALIDARG|Vyvolá, když jeden z argumentů poskytnutý metodě je neplatný.|  
|InvalidCastException|E_NOINTERFACE|Vyvolá, když typ nelze převést na jiný typ.|  
|NotImplementedException –|E_NOTIMPL|Vygeneruje se, pokud není implementovaný pro třídu metodu rozhraní.|  
|NullReferenceException|E_POINTER|Vygeneruje se při pokusu o dereference odkaz objektu null.|  
|OperationCanceledException|E_ABORT|Vyvolá, když operace byla přerušena.|  
|OutOfBoundsException|E_BOUNDS|Vygeneruje se, když se operace pokusí o přístup k datům mimo platný rozsah.|  
|OutOfMemoryException|E_OUTOFMEMORY|Vyvolá, když není dostatek paměti pro dokončení operace.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

## <a name="ctor"></a> COMException::COMException – konstruktor
Intializes novou instanci třídy COMException.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
COMException( int hresult )  
```  
  
### <a name="parameters"></a>Parametry  
 HRESULT  
 Chyba HRESULT, která je reprezentována výjimku.  
  


## <a name="hresult"></a> Vlastnost COMException::HResult
HRESULT, která odpovídá výjimku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 Hodnota HRESULT, která určuje chyba.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, jak interpretovat hodnota HRESULT najdete v tématu [struktura kódy chyb COM](http://go.microsoft.com/fwlink/p/?LinkId=262045).  

## <a name="message"></a> Vlastnost COMException::Message
Zpráva, která popisuje výjimku.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:property String^ Message {    String^ get();}  
```  
  
### <a name="property-value"></a>Hodnota vlastnosti  
 Popis výjimky.  
    

## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)