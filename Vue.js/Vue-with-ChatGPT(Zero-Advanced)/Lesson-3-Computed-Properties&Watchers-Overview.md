# VueJS - Zero to Advanced Learning Path

## Lesson 3 — Computed Properties & Watchers (Overview)

### Computed Properties

1. **Why We Need Computed & Watch**

   Methods are not ideal for everything

   Three Types of Logic in Components:

   | Type                | Purpose                                   |
   | ------------------- | ----------------------------------------- |
   | Methods             | Direct actions (events, imperative logic) |
   | Computed Properties | Derived data (cached, reactive)           |
   | Watchers            | Observing data changes for side effects   |

   Computed is for **data transformation**. Watch is for **side effects**.

2. **Computed Properties**

   Computed properties are cached based on their dependencies (**reactive cached value**).

   They only re-evaluate when their dependencies change.

   Example:

   ```javascript
   computed: {
     reversedMessage() {
       return this.message.split('').reverse().join('');
     }
   }
   ```

   Q: Why use computed instead of methods?

   A: Computed values are **cached**. A method runs **every time** the template re-renders.

3. **Computed vs Methods Example**

   **Using Method**:

   ```html
   <div>{{ reversedMessage() }}</div>
   ```

   ```javascript
   methods: {
     reversedMessage() {
       return this.message.split('').reverse().join('');
     }
   }
   ```

   **Using Computed Property**:

   ```html
   <div>{{ reversedMessage }}</div>
   ```

   ```javascript
   computed: {
     reversedMessage() {
       return this.message.split('').reverse().join('');
     }
   }
   ```

   **Behavior Comparison**:

   | Event                   | Methods    | Computed   |
   | ----------------------- | ---------- | ---------- |
   | Initial render          | Runs       | Runs       |
   | Unrelated state changes | Runs again | Uses cache |
   | Dependent state changes | Runs       | Runs       |

   Computed is more efficient and reactive-aware.

4. **Computed Getters & Setters**

   Computed properties can have both getters (`get`) and setters (`set`).

   Example:

   ```javascript
   computed: {
     fullName: {
       get() {
         return this.firstName + ' ' + this.lastName;
       },
       set(newValue) {
         const names = newValue.split(' ');
         this.firstName = names[0];
         this.lastName = names[names.length - 1];
       }
     }
   }
   ```

   Now this works: `this.fullName = 'John Doe'`

5. **Common Use Cases for Computed Properties**

   Use computed for:

   - Formatted values (prices, names, dates)
   - Filtering and searching lists
   - Combining data from multiple fields
   - Conditional classes
   - Enabling/disabling buttons

   Example:

   ```javascript
   computed: {
     isFormValid() {
       return this.email.includes('@') && this.password.length >= 6;
     }
   }
   ```

### Watchers

1. **Introduction to Watchers**

   Watchers allow you to **run code when a value changes**.

   Use when you need:

   - API calls
   - Debounced search
   - Local storage updates
   - Syncing two values
   - Logging data changes

   Example:

   ```javascript
   watch: {
     searchQuery(newQuery, oldQuery) {
       this.fetchResults(newQuery);
     }
   }
   ```

2. **Deep Watchers**

   Useful for objects & arrays

   ```javascript
   watch: {
     user: {
       handler(newUser) {
         console.log('User changed:', newUser);
       },
       deep: true
     }
   }
   ```

3. **Immediate Watchers**

   Run the watcher immediately on component creation (on load)

   ```javascript
   watch: {
     searchQuery: {
       handler(newQuery) {
         this.fetchResults(newQuery);
       },
       immediate: true
     }
   }
   ```

4. **Watch vs Computed vs Methods**

   | Feature                   | Computed | Watch | Methods            |
   | ------------------------- | -------- | ----- | ------------------ |
   | Cached                    | Yes      | No    | No                 |
   | Reactive                  | Yes      | Yes   | Only when executed |
   | Side effects              | No       | Yes   | Possible           |
   | Use for transforming data | Yes      | No    | Sometimes          |
   | Use for async / API       | No       | Yes   | No                 |

   Note: When to Use What:

   - Use **computed** for derived data that needs to be displayed.
   - Use **watch** for side effects when data changes.
   - Use **methods** for direct actions and event handling.

5. **Mini Project — Real-time Price Calculator**

   **Template**

   ```html
   <div>
     <label
       >Price:
       <input v-model.number="price" type="number" />
     </label>
     <label
       >Quantity:
       <input v-model.number="quantity" type="number" />
     </label>
     <div>Total: {{ totalPrice }}</div>
   </div>
   ```

   **Script**

   ```js
   export default {
     data() {
       return {
         price: 0,
         quantity: 0,
       };
     },
     computed: {
       totalPrice() {
         return this.price * this.quantity;
       },
     },
   };
   ```

6. **Bonus Project — Search Filter with Watch**

   **Template**

   ```html
   <div>
     <input v-model="searchQuery" placeholder="Search items..." />
     <ul>
       <li v-for="item in filteredItems" :key="item.id">{{ item.name }}</li>
     </ul>
   </div>
   ```

   **Script**

   ```js
   export default {
     data() {
       return {
         searchQuery: "",
         items: [
           { id: 1, name: "Apple" },
           { id: 2, name: "Banana" },
           { id: 3, name: "Orange" },
           { id: 4, name: "Grapes" },
         ],
         filteredItems: [],
       };
     },
     watch: {
       searchQuery(newQuery) {
         this.filteredItems = this.items.filter((item) =>
           item.name.toLowerCase().includes(newQuery.toLowerCase())
         );
       },
     },
     created() {
       // Initialize filteredItems
       this.filteredItems = this.items;
     },
   };
   ```
