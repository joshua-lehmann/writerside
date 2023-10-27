---
title: Building Block View
---

# Data Fetching
For Data fetching use a REST API provided by the [backend](building-block-view.md#backend).

## Frontend Data Fetching
In the frontend we use a library called [Tanstack Query](https://tanstack.com/query/latest) which simplifies the common data fetching tasks a lot.

### Example


```Typescript
async function getCurriculums(): Promise<Curriculum[]> {
    const { data } = await axios.get<CurriculumResponse[]>(`${import.meta.env.VITE_BACKEND_API_URL}/curriculums`); 
    return data.map((curriculum) => ({ value: curriculum.title, label: curriculum.title, year: curriculum.year }));
}

const {
    isLoading: curriculumsLoading,
    error: curriculumsError,
    data: curriculumsData,
} = useQuery({
    queryKey: ['curriculums'], // (1)
    queryFn: getCurriculums,
});

if (yearsLoading || curriculumsLoading) {
        return <h2>Loading</h2>;
    }
```


<tabs>
<tab title="Typescript">

```Typescript
async function getCurriculums(): Promise<Curriculum[]> {
    const { data } = await axios.get<CurriculumResponse[]>(`${import.meta.env.VITE_BACKEND_API_URL}/curriculums`); 
    return data.map((curriculum) => ({ value: curriculum.title, label: curriculum.title, year: curriculum.year }));
}

const {
    isLoading: curriculumsLoading,
    error: curriculumsError,
    data: curriculumsData,
} = useQuery({
    queryKey: ['curriculums'], // (1)
    queryFn: getCurriculums,
});

if (yearsLoading || curriculumsLoading) {
        return <h2>Loading</h2>;
    }
```
</tab>

<tab title="JavaScript">

```Javascript title="Onboarding.jsx"
    async function getCurriculums() {
        const { data } = await axios.get(`${import.meta.env.VITE_BACKEND_API_URL}/curriculums`); 
        return data.map((curriculum) => ({ value: curriculum.title, label: curriculum.title, year: curriculum.year }));
    }

    const {
        isLoading: curriculumsLoading,
        error: curriculumsError,
        data: curriculumsData,
    } = useQuery({
        queryKey: ['curriculums'], // (1)
        queryFn: getCurriculums,
    });

    if (yearsLoading || curriculumsLoading) {
            return <h2>Loading</h2>;
        }
```

</tab>
</tabs>

## Backend API
Endpoints for the course resource
<api-doc openapi-path="../images/assets/SmashGradeSwagger.yml" tag="kurs"></api-doc>



