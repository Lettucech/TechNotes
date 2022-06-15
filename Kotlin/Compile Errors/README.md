# Compile Errors
## Unbound symbols not allowed
### Case: Emitting a "If-not-null-else shorthand" statement in Kotlin Flow
```kotlin
suspend fun getProducts() = flow {
    emit(productApi.getProducts() ?: emptyList())
}
```
#### Error
```
java.lang.AssertionError: Unbound symbols not allowed

Unbound private symbol org.jetbrains.kotlin.ir.symbols.impl.IrClassSymbolImpl@adc7be5 (NON-PUBLIC API): <ERROR CLASS>
	at org.jetbrains.kotlin.ir.util.SymbolTableKt.noUnboundLeft(SymbolTable.kt:1124)
	at org.jetbrains.kotlin.psi2ir.Psi2IrTranslator.generateModuleFragment(Psi2IrTranslator.kt:87)
	at org.jetbrains.kotlin.backend.jvm.JvmIrCodegenFactory.convertToIr(JvmIrCodegenFactory.kt:146)
	at org.jetbrains.kotlin.backend.jvm.JvmIrCodegenFactory.convertToIr$default(JvmIrCodegenFactory.kt:64)
	at org.jetbrains.kotlin.backend.jvm.JvmIrCodegenFactory.generateModule(JvmIrCodegenFactory.kt:59)
	...
```
#### Solution
```kotlin
suspend fun getProducts() = flow {
    val list = productApi.getProducts() ?: emptyList()
    emit(list)
}
```
