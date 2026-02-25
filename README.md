# Todo Application

## Instructions

1. Clone this repository:

```
git clone https://github.com/journi-uk/frontend-challenge-vue
```

2. Install dependencies:

```
npm install
```

3. Run the app:

```
npm run dev
```

4. Complete the tasks described below.

## Evaluation Criteria

### Component Structure & Code Organization

- Clear folder structure and separation of concerns
- Proper modularity of Vue components (e.g., splitting `TodoList` into smaller components)
- Code reusability and maintainability
- Correct use of TypeScript types and interfaces (`Task`, API payloads)
- Idiomatic Vue patterns (`defineProps`, `defineEmits`, composables when needed)

### Reactivity, State Management & API Integration

- Correct use of Vue reactivity (`ref`, `reactive`, `computed`, `watch`)
- API integration with correct HTTP methods (GET, POST, DELETE)
- Handling of loading, success, and error states in API calls

### Styling & Accessibility

- Clean and consistent styling (CSS modules, Tailwind, Styled Components, etc.)
- Fully responsive UI
- Correct use of semantic HTML for accessibility

### Error Handling & User Feedback

- Form validation to prevent empty tasks
- API error handling with proper messages
- Graceful user feedback on failures (e.g., toast notifications)

### Bonus Points

- Proper state organization (local state, composables, or Pinia)
- Unit tests for key components/composables
- Efficient and correct reactive updates
- Reusable composables for async logic
- Additional improvements beyond the requirements

## Tasks

### Basic Requirements

- [ ] Implement task deletion functionality
- [ ] Add form validations to prevent empty or whitespace-only tasks
- [ ] Refactor `TodoList` to be more modular (split into smaller Vue components)
- [ ] Implement API integration to get tasks
- [ ] Implement API integration to add and delete tasks
- [ ] Implement proper TypeScript types and interfaces
- [ ] Improve task list styles -
      [Figma](https://www.figma.com/design/mrnJCCIfjn70jlxtFFkrGX/Sample-UI?node-id=0-1&p=f&m=dev)

### Bonus track (optional)

- [ ] Add loading states
- [ ] Improve accessibility and target 100% Lighthouse accessibility score
- [ ] Implement state management using composables or Pinia
- [ ] Write unit tests for components/composables
- [ ] Implement infinite scrolling or pagination

### API Endpoints

| Method     | Endpoint                                               | Description                    |
| ---------- | ------------------------------------------------------ | ------------------------------ |
| **GET**    | `https://retoolapi.dev/xaoo5W/tasks`                   | Get all tasks                  |
| **GET**    | `https://retoolapi.dev/xaoo5W/tasks?Name=value`        | Get tasks filtered by Name     |
| **GET**    | `https://retoolapi.dev/xaoo5W/tasks/1`                 | Get task by ID                 |
| **GET**    | `https://retoolapi.dev/xaoo5W/tasks?_page=2&_limit=10` | Get paginated tasks            |
| **POST**   | `https://retoolapi.dev/xaoo5W/tasks`                   | Create a new task              |
| **PUT**    | `https://retoolapi.dev/xaoo5W/tasks/1`                 | Replace a task (full update)   |
| **PATCH**  | `https://retoolapi.dev/xaoo5W/tasks/1`                 | Update a task (partial update) |
| **DELETE** | `https://retoolapi.dev/xaoo5W/tasks/1`                 | Delete a task                  |

