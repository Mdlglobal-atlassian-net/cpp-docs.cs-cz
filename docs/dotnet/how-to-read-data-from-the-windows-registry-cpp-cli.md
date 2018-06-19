---
title: 'Postupy: čtení dat z registru systému Windows (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, reading from Windows Registry
- registry, reading
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87c882bcf2a7900e1f95ea968407c159333c6cb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132551"
---
# <a name="how-to-read-data-from-the-windows-registry-ccli"></a>Postupy: Čtení dat z registru systému Windows (C++/CLI)
Následující příklad kódu používá <xref:Microsoft.Win32.Registry.CurrentUser> klíč číst data z registru systému Windows. Nejprve podklíčů jsou uvedené pomocí <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> metoda a pak je podklíč identity je otevřena pomocí <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metoda. Podobně jako kořenového klíče, je reprezentována každý podklíč <xref:Microsoft.Win32.RegistryKey> třídy. Nakonec novou <xref:Microsoft.Win32.RegistryKey> objekt se používá k vytvoření výčtu páry klíč/hodnota.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 <xref:Microsoft.Win32.Registry> Třída slouží pouze jako kontejner pro statické instance <xref:Microsoft.Win32.RegistryKey>. Jednotlivé instance představují kořenový uzel registru. Instance jsou <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, a <xref:Microsoft.Win32.Registry.Users>.  
  
 Kromě toho stal statické, objektů v rámci <xref:Microsoft.Win32.Registry> třídy jsou jen pro čtení. Kromě toho instance služby <xref:Microsoft.Win32.RegistryKey> třídu, která jsou vytvořeny pro přístup k obsahu registru objekty jsou jen pro čtení i. Příklad toho, jak toto chování potlačit, naleznete v části [postupy: zápis dat do registru systému Windows (C + +/ CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).  
  
 Ve třídě <xref:Microsoft.Win32.Registry> existují dva další objekty: <xref:Microsoft.Win32.Registry.DynData> a <xref:Microsoft.Win32.Registry.PerformanceData>. Jsou obě instance <xref:Microsoft.Win32.RegistryKey> třídy. <xref:Microsoft.Win32.Registry.DynData> Obsahuje informace o dynamické registru, který je podporován pouze v systému Windows 98 a Windows Me. <xref:Microsoft.Win32.Registry.PerformanceData> Objekt lze použít pro přístup k informacím čítače výkonu pro aplikace, které používají systém monitorování výkonu systému Windows. <xref:Microsoft.Win32.Registry.PerformanceData> Informace, které není ve skutečnosti uloženy v registru a proto nelze zobrazit, pomocí Regedit.exe představuje uzel.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: zápis dat do registru systému Windows (C + +/ CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Operace systému Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)