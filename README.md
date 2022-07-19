# Strategy-Pattern-with-Swift
Here is a simple example of Strategy design pattern in Swift 

# The Strategy pattern lets you indirectly alter the object's behavior at runtime by associating it with different sub-objects which can perform specific sub-tasks in different ways. Use the Strategy when you have a lot of similar classes that only differ in the way they execute some behavior.
## or simply we use this pattern moslty to avoid the large if / elase conditions.
# You can also download the demo project in Playground.
    
    protocol TranslationStrategy {
        func translate(text: String)
    }
    
    class Translator {
    
        private var strategy: TranslationStrategy
    
        init(strategy: TranslationStrategy) {
            self.strategy = strategy
        }
    
        func update(strategy: TranslationStrategy) {
            self.strategy = strategy
        }
    
        func translate(text: String) {
            strategy.translate(text: text)
        }
    }
    
    class GermanyStrategy: TranslationStrategy {
    
        func translate(text: String) {
            print("Germany strategy will translate: \(text)")
        }
    }
    
    class SpanishStrategy: TranslationStrategy {
    
        func translate(text: String) {
            print("Spanish strategy will translate: \(text)")
        }
    }
    
    // MARK: - Usage
    
    let translator = Translator(strategy: GermanyStrategy())
    translator.translate(text: "ha ha")
    
    translator.update(strategy: SpanishStrategy())
    translator.translate(text: "ha ha")
    
