# Rage Damage
*By Theodore#7790.*

### Usage
`!a [weapon] ra` 

### Setup
Run the command in the Code section. It will automatically add your rage damage to your attack. **Note**: It does increase with level.

### Code
```GN
!snippet ra -d "{{floor(level/9)+floor(level/16)-floor(level/18)+2}}"
```
