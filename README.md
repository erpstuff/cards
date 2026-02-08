# ERPStuff Cards - Oracle APEX Template Component Plugin

A modern, responsive card-based template component plugin for Oracle APEX that displays dashboard metrics and KPIs with smooth animations, customizable styling, and interactive features.

## Features

- **Responsive Grid Layout**: Automatically adjusts card layout based on screen size
- **Customizable Design**: Control colors, icons, sizes, and spacing
- **Smooth Animations**: Hover effects and optional pulse animations for important metrics
- **Action Buttons**: Support for clickable cards with action buttons
- **Font Awesome Icons**: Full support for Font Awesome icons
- **Flexible Styling**: Modern glassmorphism effects with rounded corners and shadows
- **Easy Configuration**: Simple attribute-based configuration

## Installation

1. Download the plugin file
2. Navigate to **Shared Components > Plug-ins** in your Oracle APEX application
3. Click **Import**
4. Select the plugin file and follow the import wizard
5. Click **Install Plug-in**

## Configuration

### Plugin Attributes

#### Component Level Attributes (Per Card)
- **Title** (Required): Card title text
- **Card Body** (Required): Main content/value to display
- **Footer Text**: Optional footer text for additional context
- **Card Icon**: Font Awesome icon class (e.g., 'fa-dollar', 'fa-users')
- **Card Color**: Background color in hex format (e.g., '#10b981')
- **Card Font Color**: Text color in hex format (e.g., '#ffffff')
- **Card Animation**: Animation type ('pulse' for green, 'pulse-warning' for red, null for none)
- **Card Link**: URL for action button navigation

#### Region Level Attributes (Applies to All Cards)
- **Cards Per Row**: Number of cards to display per row (default: 4)
- **Cards Gap**: Spacing between cards in pixels (default: 5)
- **Icon Size**: Icon container size (default: 60px)
- **Card Height**: Minimum card height (default: 200px)

## Usage Example

### Basic SQL Query
```sql
SELECT 1 ID,
        'Total Revenue' as TITLE,
        '$125,450' as CARD_BODY,
        '+18% from last month' as FOOTER_TEXT,
        'fa-dollar' as CARD_ICON,
        '#10b981' as CARD_COLOR,
        '#ffffff' as CARD_FONT_COLOR,
        apex_page.get_url(p_page => 2) as CARD_LINK,
        'pulse' as CARD_ANIMATION
 FROM DUAL
union
 SELECT 2 ID,
       'Total Expenses' as TITLE,
       '$42,890' as CARD_BODY,
       '+5% from last month' as FOOTER_TEXT,
       'fa-credit-card' as CARD_ICON,
       '#ef4444' as CARD_COLOR,
       '#ffffff' as CARD_FONT_COLOR,
       apex_page.get_url(p_page => 3) as CARD_LINK,
       null as CARD_ANIMATION
 FROM DUAL
```

### Dynamic Data Example
```sql
SELECT employee_id as ID,
       department_name as TITLE,
       TO_CHAR(total_salary, '$999,999') as CARD_BODY,
       employee_count || ' employees' as FOOTER_TEXT,
       'fa-users' as CARD_ICON,
       CASE 
         WHEN total_salary > 100000 THEN '#10b981'
         WHEN total_salary > 50000 THEN '#3b82f6'
         ELSE '#f59e0b'
       END as CARD_COLOR,
       '#ffffff' as CARD_FONT_COLOR,
       apex_page.get_url(p_page => 10, p_items => 'P10_DEPT_ID', p_values => department_id) as CARD_LINK,
       CASE WHEN total_salary > 150000 THEN 'pulse' ELSE null END as CARD_ANIMATION
  FROM department_summary
```

## Region Settings

1. Create a new **Region**
2. Set **Type** to **ERPStuff Cards** (or your plugin name)
3. Set **Source > Type** to **SQL Query**
4. Enter your SQL query
5. Configure region attributes:
   - Cards Per Row: 4
   - Cards Gap: 5
   - Icon Size: 60px
   - Card Height: 200px

## Customization

### Color Schemes

**Success/Positive** (Green tones):
- `#10b981`, `#22c55e`, `#86efac`

**Warning/Attention** (Orange/Yellow):
- `#f59e0b`, `#fcd34d`, `#fb923c`

**Error/Negative** (Red tones):
- `#ef4444`, `#fca5a5`, `#dc2626`

**Info/Neutral** (Blue tones):
- `#3b82f6`, `#93c5fd`, `#06b6d4`

### Font Awesome Icons

Common dashboard icons:
- Revenue/Money: `fa-dollar`, `fa-money`, `fa-coins`
- Users: `fa-users`, `fa-user`, `fa-user-plus`
- Charts: `fa-chart-line`, `fa-bar-chart`, `fa-area-chart`
- Orders: `fa-shopping-cart`, `fa-shopping-bag`
- Projects: `fa-folder-open`, `fa-tasks`, `fa-project-diagram`
- Alerts: `fa-bell`, `fa-exclamation-triangle`
- Growth: `fa-arrow-up`, `fa-trending-up`

## Animation Types

- **pulse**: Green glowing animation for positive metrics
- **pulse-warning**: Red glowing animation for alerts/warnings
- **null**: No animation (default)

## Best Practices

1. **Limit Cards Per Row**: Use 3-6 cards per row for optimal readability
2. **Consistent Heights**: Set Card Height to ensure uniform appearance
3. **Color Coding**: Use consistent colors for similar metric types
4. **Meaningful Icons**: Choose icons that represent the metric
5. **Concise Text**: Keep titles short and footer text informative
6. **Responsive Design**: Test on different screen sizes
7. **Animation Sparingly**: Use animations only for critical metrics

## Browser Compatibility

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Support

For issues, questions, or feature requests:
- Website: https://erpstuff.com
- Community: ERPStuff Oracle APEX Community

## Version History

**v1.0.0** - Initial Release
- Responsive card layout
- Customizable colors and icons
- Hover animations
- Pulse animations
- Action button support

## License

Created by Sikandar Ali (ERPStuff.com)
Oracle ACE Pro

## Credits

- Oracle APEX Team
- Font Awesome Icons
- ERPStuff Community
