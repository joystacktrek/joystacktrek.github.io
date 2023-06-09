# PYTHON TO JAVASCRIPT: A QUICK PRIMER

As you transition from Python to JavaScript, you will be introduced to a language with slight difference in syntax. This chapter will act as a transition primer for you to apply the knowledge and skills you've learned in Python. 

Take note of the highlighted differences:
1. In Python, varaibles are declared using `snake_case`, whereas JavaScript delcares using `camelCase`
2. In Python, immutable variables (*constants*) are implicitly declared using `UPPERCASE`, whereas JavaScript has explicit immutability through the `const` keyword (though it's behavior is different for arrays and objects)
3. In Python, indentation matters and serves as the primary way your code is interpreted, whereas, in JavaScript, scope is defined with curly braces {}  and semi-colons* ; separating expressions and statements
4. In leiu of Python's `f-strings` (*f in front of quotation marks with curly brackets {} for variables*), JavaScript instead uses `Template Literals` (*backticks with ${} for variables*)
5. In JavaScript, functions are considered first-class objects (like numbers, strings, and objects). They can also be declared in multiple ways such as arrow functions (See CELLPHONE PLAN)


## The following table shows you some previously answered questions translated into JavaScript as functions:
> NOTE: Input is handled differently in JavaScript, which is usually handled in the company of HTML, so, for comparison's sake, all questions will be in the form of callable functions or objects
<table>
<tr>
    <th style="text-align: center;"><h2>Problem</h2></th>
    <th style="text-align: center;"><h2>Python</h2></th>
    <th style="text-align: center;"><h2>JavaScript</h2></th>
</tr>
<tr>
<td>HYPOTENUSE</td>

<td>

```python
def hypotenuse(side_1, side_2):
    result = (side_1 ** 2) + (side_2 ** 2)
    return result


```

</td>


<td>

```js
function hypotenuse(side1, side2) { 
  const result = (side1 ** 2) + (side2 ** 2)
  return result
}

```

</td>

</tr>
<tr>
<td>TAXI</td>

<td>
 
```python
def taxi(distance):
    BASE = 4
    excess = distance / 140
    if excess > 1:
        result = excess * 0.25 + BASE
        return "%.2f" % result
    else:
        return "4.00"


```

</td>


<td>

```js
function taxi(distance) { 
  const BASE = 4
  let excess = distance / 140
  if (excess > 1) {
    let result = excess * 0.25 + BASE
    return result.toFixed(2)      
  } else {
    return “4.00” 
  }
}
```

</td>

</tr>
<tr>
<td>CELLPHONE PLAN</td>

<td>

```python
def cellphone_plan(call_minutes, text_messages):
    BASE_PLAN = 799.00
    EMERGENCY_FEE = 25.00
    excess_minutes = 0
    excess_texts = 0

    if call_minutes > 60:
        excess_minutes = (call_minutes - 60) * 6.50
    if text_messages > 100:
        excess_minutes = text_messages - 100

    total_bill = BASE_PLAN + excess_minutes + excess_texts + EMERGENCY_FEE
    tax = total_bill * 0.05
    total_bill += tax

    return f"Call minutes: {call_minutes}\nText messages: {text_messages}\nExcess minute charges: {excess_minutes:.2f}\nExcess SMS charges: {excess_texts:.2f}\n911 fee: {EMERGENCY_FEE}\nTax: {tax:.2f}"
```

</td>


<td>

```js
const cellphonePlan = (callMinutes, textMessages) => {
    const basePlan = 799.00
    const emergencyFee = 25.00

    let excessMinutes = 0
    let excessTexts = 0

    if (callMinutes > 60) excessMinutes = (callMinutes - 60) * 6.50
    if (textMessages > 100) excessTexts = textMessages - 100

    let totalBill = basePlan + excessMinutes + excessTexts + emergencyFee
    const tax = totalBill * 0.05
    totalBill += tax

    return `Call minutes: ${callMinutes}\nText messages: ${textMessages}\nExcess minute charges: ${excessMinutes.toFixed(2)}\nExcess SMS charges: ${excessTexts.toFixed(2)}\n911 fee: ${emergencyFee.toFixed(2)}\nTax: ${tax.toFixed(2)}`
}
```

</td>

</tr>

<tr>
<td>MAN'S BEST FRIEND</td>
<td>

```python
class Dog:
	def __init__(self, name, breed):
		self.name = name
		self.breed = breed

	def bark(self):
		return f"{self.name} is barking"

	def run(self):
		return f"{self.name} is running"

	def eat(self, food):
		return f"{self.name} is eating {food}"

	def play(self, object):

		if object[0].lower().startswith(("a", "e", "i", "o", "u")):
			return f"{self.name} is playing with an {object}"

		return f"{self.name} is playing with a {object}"






```

</td>
<td>

```js
class Dog  {
    constructor(name, breed) {
        this.name = name
        this.breed = breed
    }

    bark() {
        return `${this.name} is barking`
    }

    run() {
        return `${this.name} is running`
    }

    eat(food) {
        return `${this.name} is eating ${food}`
    }

    play(object) {
        if (['a', 'e', 'i', 'o', 'u'].includes(object[0].toLower())) {
            return `${this.name} is playing with an ${object}`
        }

        return `${this.name} is playing with a ${object}`
    }
}
```

</td>

</tr>

<tr>
<td>SHIP ME</td>
<td>

```python
class Package:

    def __init__(self, weight, distance):
        self._weight = weight
        self._distance = distance

    @property
    def weight(self):
        return self._weight

    @weight.setter
    def weight(self, value):
        self._weight = value
        self.added_shipping_tax = value

    @property
    def distance(self):
        return self._distance

    @distance.setter
    def distance(self, value):
        self._distance = value
        self.shipping_fee = value

    @property
    def shipping_fee(self):
        return self._shipping_fee

    @shipping_fee.setter
    def shipping_fee(self, distance):
        if distance < 2:
            self._shipping_fee = 0
        elif distance < 100:
            self._shipping_fee = 45
        else:
            mile_price = (distance // 100) * 50
            extra = (distance % 100) * 1.50
            self._shipping_fee = mile_price + extra

    @property
    def added_shipping_tax(self):
        return self._added_shipping_tax

    @added_shipping_tax.setter
    def added_shipping_tax(self, weight):
        if weight >= 1:
            tax_amount = weight * 0.25
            self._added_shipping_tax = tax_amount
        else:
            self._added_shipping_tax = 0

    @property
    def total_shipping_fee(self):
        self._total_shipping_fee = self._shipping_fee + self._added_shipping_tax

        return round(self._total_shipping_fee, 2)

```

</td>
<td>

```js
class Package {
    constructor(weight, distance) {
        this._weight = weight
        this._distance = distance
    }

    get weight() {
        return this._weight
    }

    set weight(value) {
        this._weight = value
        this._addedShippingTax = value
    }

    get distance() {
        return this._distance
    }

    set distance(value) {
        this._distance = value
        this._shippingFee = value
    }

    get shippingFee() {
        return this._weight
    }

    set shippingFee(distance) {
        if (distance < 2) {
            this._shippingFee = 0
        } 
        else if (distance < 100) {
            this._shippingFee = 45
        } else {
            const milePrice = Math.round(distance / 100) * 50
            const extra = (distance % 100) * 1.50
            this._shippingFee = milePrice + extra
        }
    }

    get addedShippingTax() {
        return this._addedShippingTax
    }

    set addedShippingTax(weight) {
        this._addedShippingTax = (weight >= 1)
            ? weight * 0.25
            : 0
    }

    get totalShippingFee() {
        this._totalShippingFee = this._shippingFee + this.addedShippingTax
        return round(this._totalShippingFee, 2)
    }
}

```

</td>

</tr>
</table>
