---
title: CDataConnection – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: 8bd31070588f80c29589767ef68b221bf15f0570
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482751"
---
# <a name="cdataconnection-class"></a>CDataConnection – třída

Spravuje připojení ke zdroji dat.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataConnection
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Cdataconnection –](#cdataconnection)|Konstruktor Vytvoří a inicializuje `CDataConnection` objektu.|
|[kopírování](#copy)|Vytvoří kopii existující datové připojení.|
|[Otevřít](#open)|Otevře připojení ke zdroji dat pomocí inicializačního řetězce.|
|[Opennewsession –](#opennewsession)|Otevře se nová relace pro aktuální připojení.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[BOOL – operátor](#op_bool)|Určuje, zda aktuální relace je otevřený, nebo ne.|
|[bool – operátor](#op_bool_ole)|Určuje, zda aktuální relace je otevřený, nebo ne.|
|[operátor CDataSource &](#op_cdata_amp)|Vrátí odkaz na obsaženého objektu `CDataSource` objektu.|
|[operátor CDataSource *](#op_cdata_star)|Vrací ukazatel na obsaženého objektu `CDataSource` objektu.|
|[operátor CSession &](#op_csession_amp)|Vrátí odkaz na obsaženého objektu `CSession` objektu.|
|[operátor CSession *](#op_csession_star)|Vrací ukazatel na obsaženého objektu `CSession` objektu.|

## <a name="remarks"></a>Poznámky

`CDataConnection` je užitečné třída pro vytvoření klientů, protože zapouzdřuje nezbytných objektů (zdroj dat a relace) a některé činnosti, které je třeba provést při připojování ke zdroji dat

Bez `CDataConnection`, je nutné vytvořit `CDataSource` objektů, zavolejte jeho [OpenFromInitializationString –](../../data/oledb/cdatasource-openfrominitializationstring.md) metodu, vytvořte instanci [CSession](../../data/oledb/csession-class.md) objektu, volejte jeho [ Otevřít](../../data/oledb/csession-open.md) metodu, vytvořte [CCommand](../../data/oledb/ccommand-class.md) objektu a volání jeho `Open`* metody.

S `CDataConnection`, je třeba pouze vytvořit objekt připojení, předat ji inicializačního řetězce a pak používat toto připojení otevřete příkazy. Pokud máte v úmyslu používat připojení k databázi opakovaně, je vhodné ponechat otevřené, připojení a `CDataConnection` poskytuje pohodlný způsob, jak to udělat.

> [!NOTE]
>  Pokud vytváříte databázovou aplikaci, kterou je potřeba zpracovat více relací, budete muset použít [opennewsession –](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="#cdataconnection"></a> CDataConnection::CDataConnection

Vytvoří a inicializuje `CDataConnection` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection(); 
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parametry

*adresářové služby*<br/>
[in] Odkaz na existující datové připojení.

### <a name="remarks"></a>Poznámky

Vytvoří novou první přepsání `CDataConnection` objektu s výchozím nastavením.

Druhý přepsání vytvoří novou `CDataConnection` objekt s ekvivalentní objekt datového připojení, můžete zadat nastavení.

## <a name="#copy"></a> CDataConnection::Copy

Vytvoří kopii existující datové připojení.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parametry

*adresářové služby*<br/>
[in] Odkaz na existující datové připojení ke kopírování.

## <a name="#open"></a> CDataConnection::Open

Otevře připojení ke zdroji dat pomocí inicializačního řetězce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parametry

*szInitString*<br/>
[in] Inicializační řetězec pro zdroj dat.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="#opennewsession"></a> CDataConnection::OpenNewSession

Otevře se nová relace pomocí zdroje dat aktuální objekt připojení.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parametry

*Relace*<br/>
[/ out] Odkaz na objekt novou relaci.

### <a name="remarks"></a>Poznámky

Novou relaci používá aktuální objekt připojení objekt zdroje dat obsažených jako jeho nadřazeným prvkem a mít přístup ke všem stejné informace jako zdroj dat.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="op_bool"></a> CDataConnection::operator BOOL

Určuje, zda aktuální relace je otevřený, nebo ne.

### <a name="syntax"></a>Syntaxe

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí **BOOL** hodnotu (MFC typedef). **Hodnota TRUE** znamená, že aktuální relace je otevřená. **FALSE** znamená, že aktuální relace je ukončena.

## <a name="op_bool_ole"></a> CDataConnection::operator bool (OLE DB)

Určuje, zda aktuální relace je otevřený, nebo ne.

### <a name="syntax"></a>Syntaxe

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí **bool** hodnotu (C++ datový typ). **Hodnota TRUE** znamená, že aktuální relace je otevřená. **false** znamená, že aktuální relace je ukončena.

## <a name="op_cdata_amp"></a> CDataConnection::operator CDataSource&amp;

Vrátí odkaz na obsaženého objektu `CDataSource` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí odkaz na obsaženého objektu `CDataSource` objektu, abyste mohli předat `CDataConnection` objekt kde `CDataSource` očekává odkaz.

### <a name="example"></a>Příklad

Pokud máte funkci (jako `func` níže), která má `CDataSource` reference, můžete použít `CDataSource&` předat `CDataConnection` namísto toho objekt.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a> CDataConnection::operator CDataSource *

Vrací ukazatel na obsaženého objektu `CDataSource` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí ukazatel obsaženého objektu `CDataSource` objektu, abyste mohli předat `CDataConnection` objekt kde `CDataSource` očekává ukazatel.

Zobrazit [operátor CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) například využití.

## <a name="op_csession_amp"></a> CDataConnection::operator CSession&amp;

Vrátí odkaz na obsaženého objektu `CSession` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí odkaz na obsaženého objektu `CSession` objektu, abyste mohli předat `CDataConnection` objekt kde `CSession` očekává odkaz.

### <a name="example"></a>Příklad

Pokud máte funkci (jako `func` níže), která má `CSession` reference, můžete použít `CSession&` předat `CDataConnection` namísto toho objekt.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a> CDataConnection::operator CSession *

Vrací ukazatel na obsaženého objektu `CSession` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí ukazatel obsaženého objektu `CSession` objektu, abyste mohli předat `CDataConnection` objekt kde `CSession` očekává ukazatel.

### <a name="example"></a>Příklad

Zobrazit [operátor CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) například využití.

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)