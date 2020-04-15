---
title: FtmBase – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: d37cdddda8cf8894016ed80b9055fe106b1600f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371516"
---
# <a name="ftmbase-class"></a>FtmBase – třída

Představuje objekt zařazovače volných vláken.

## <a name="syntax"></a>Syntaxe

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [RuntimeClass Class Class](runtimeclass-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

| Name (Název)                         | Popis                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase::FtmBase](#ftmbase) | Inicializuje novou instanci třídy. `FtmBase` |

### <a name="public-methods"></a>Veřejné metody

| Name (Název)                                                               | Popis                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | Vytvoří tabulku globálního rozhraní (GIT).                                                                                                                              |
| [FtmBase::DisconnectObject](#disconnectobject)                     | Násilně uvolní všechna externí připojení k objektu. Server objektu volá implementaci objektu této metody před vypnutím.                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | Získejte horní mez na počet bajtů potřebných k zařazovací ukazatel zadané ho rozhraní na zadaný objekt.                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | Získá CLSID, který com používá k vyhledání DLL obsahující kód pro odpovídající proxy server. Com načte tuto dll vytvořit neinicializované instance proxy serveru. |
| [FtmBase::MarshalInterface](#marshalinterface)                     | Zapíše do datového proudu data potřebná k inicializaci proxy objektu v některém procesu klienta.                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | Zničí zařazovaný datový paket.                                                                                                                                    |
| [FtmBase::UnmarshalInterface](#unmarshalinterface)                 | Inicializuje nově vytvořený proxy server a vrátí ukazatel rozhraní na tento proxy server.                                                                                    |

### <a name="public-data-members"></a>Veřejné datové členy

| Name (Název)                                | Popis                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase::marshaller_](#marshaller) | Obsahuje odkaz na volné podprocesové zařazování. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FtmBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ftm.h

**Obor názvů:** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

Vytvoří tabulku globálního rozhraní (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parametry

*Git*<br/>
Po dokončení této operace ukazatel na tabulku globálního rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Další informace naleznete `IGlobalInterfaceTable` v tématu v `COM Interfaces` `COM Reference` dílčím tématu tématu v knihovně MSDN.

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase::DisconnectObject

Násilně uvolní všechna externí připojení k objektu. Server objektu volá implementaci objektu této metody před vypnutím.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parametry

*dwVyhrazeno*<br/>
Vyhrazeno pro budoucí použití; musí být nula.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>FtmBase::FtmBase

Inicializuje novou instanci třídy. `FtmBase`

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

Získejte horní mez na počet bajtů potřebných k zařazovací ukazatel zadané ho rozhraní na zadaný objekt.

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
Odkaz na identifikátor rozhraní, které má být zařazeno.

*Pv*<br/>
Ukazatel rozhraní, který má být zařazen; může být null.

*dwDestKontext*<br/>
Cílový kontext, kde má být zadané rozhraní unmarshaled.

Zadejte jednu nebo více hodnot výčtu MSHCTX.

V současné době unmarshaling může dojít buď v jiném apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Vyhrazeno pro budoucí použití; musí být null.

*mshlflags*<br/>
Příznak označující, zda data, která mají být zařazena má být předána zpět do procesu klienta – typický případ – nebo zapsány do globální tabulky, kde mohou být načteny více klientů. Zadejte jednu nebo více hodnot výčtu MSHLFLAGS.

*pVelikost*<br/>
Po dokončení této operace, ukazatel na horní mez na množství dat, která mají být zapsány do zařazování proudu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_FAIL nebo E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

Získá CLSID, který com používá k vyhledání DLL obsahující kód pro odpovídající proxy server. Com načte tuto dll vytvořit neinicializované instance proxy serveru.

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
Odkaz na identifikátor rozhraní, které má být zařazeno.

*Pv*<br/>
Ukazatel na rozhraní, které má být zařazeno; může být NULL, pokud volající nemá ukazatel na požadované rozhraní.

*dwDestKontext*<br/>
Cílový kontext, kde má být zadané rozhraní unmarshaled.

Zadejte jednu nebo více hodnot výčtu MSHCTX.

Unmarshaling může dojít buď v jiném apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Vyhrazeno pro budoucí použití; musí být null.

*mshlflags*<br/>
Po dokončení této operace, ukazatel na CLSID, které mají být použity k vytvoření proxy v procesu klienta.

*pCid*

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase::MarshalInterface

Zapíše do datového proudu data potřebná k inicializaci proxy objektu v některém procesu klienta.

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Ukazatel na datový proud, který má být použit během zařazování.

*riid řekl:*<br/>
Odkaz na identifikátor rozhraní, které má být zařazeno. Toto rozhraní musí být `IUnknown` odvozeno z rozhraní.

*Pv*<br/>
Ukazatel na ukazatel rozhraní, který má být zařazen; může být NULL, pokud volající nemá ukazatel na požadované rozhraní.

*dwDestKontext*<br/>
Cílový kontext, kde má být zadané rozhraní unmarshaled.

Zadejte jednu nebo více hodnot výčtu MSHCTX.

Unmarshaling může dojít v jiném apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).

*pvDestContext*<br/>
Vyhrazeno pro budoucí použití; musí být nula.

*mshlflags*<br/>
Určuje, zda mají být data, která mají být zařazena, odeslána zpět do klientského procesu – typického případu – nebo zapsána do globální tabulky, kde je může načíst více klientů.

### <a name="return-value"></a>Návratová hodnota

S_OK Ukazatel rozhraní byl úspěšně zařazen.

E_NOINTERFACE Zadané rozhraní není podporováno.

STG_E_MEDIUMFULL Datový proud je plný.

E_FAIL Operace se nezdařila.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>FtmBase::marshaller_

Obsahuje odkaz na volné podprocesové zařazování.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

Zničí zařazovaný datový paket.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Ukazatel na datový proud, který obsahuje datový paket, který má být zničen.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase::UnmarshalInterface

Inicializuje nově vytvořený proxy server a vrátí ukazatel rozhraní na tento proxy server.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parametry

*pStm*<br/>
Ukazatel na datový proud, ze kterého má být nezařazen.

*riid řekl:*<br/>
Odkaz na identifikátor rozhraní, které má být unmarshaled.

*Ppv*<br/>
Po dokončení této operace, adresa ukazatele proměnné, která obdrží ukazatel rozhraní požadované v *riid*. Pokud je tato operace úspěšná, **ppv* obsahuje požadovaný ukazatel rozhraní rozhraní, které má být unmarshaled.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_NOINTERFACE nebo E_FAIL.
